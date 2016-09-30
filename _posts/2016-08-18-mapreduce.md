---
layout:     post
title:      MapReduce
category: blog
description: 介绍MapReduce编程模型的原理。
---

## 摘要    

MapReduce是一种处理大规模数据集的编程模型。MapReduce分为map函数和reduce函数，map函数处理key/value对并产生一堆中间key/value对，reduce函数合并同一个key对应的中间key/value对。很多现实世界的任务都可由MapReduce模型表示。以Mapduce编程模型实现的程序可以自动在大规模集群上并行执行，且不用关心分割输入数据、调度执行、机器故障和机器间通信等细节。这让不懂分布式系统的人可以轻松用上大规模分布式系统的资源。    

## 编程模型  

MapReduce模型的输入和输出都是一堆key/value对。MapReduce使用者只需要实现两个函数： Map和Reduce。 Map函数将一堆key/value对作为输入，并输出一堆中间key/value对。MapReduce将相同key值的key/value对合并后，作为Reduce函数的输入。 Reduce函数接收的参数为1个中间key值和多个value值，并合并所有这些value值。一般来说value值会通过迭代的方式提供给Reduce函数，因此可以处理大到内存装不下value列表。     

以wordcounter的程序为例，要数出一堆文档中每个单词出现的次数。伪代码如下:  

	map(String key, String value): 
		// key: document name		// value: document contents 		for each word w in value:			EmitIntermediate(w, "1");				reduce(String key, Iterator values): 		// key: a word		// values: a list of counts		int result = 0;    	for each v in values:      		result += ParseInt(v);    	Emit(AsString(result));

map函数产生每个单词和出现次数（为了简单，在本例中为1），reduce函数将一个单词出现的次数加起来。本例完整的程序会附在文后。    


## 执行过程    

多台机器并行调用Map将输入数据分成M个split，输入的分片可被不同机器并行处理。Reduce根据分区函数(partition function)和R决定最终文件输出（比如，hash(key) mod R，用户指定分区函数和R）。下图说明了用户调用MapReduce函数时，一系列发生的动作。     
![mapreduce过程](../images/mapreduce/mapreduce1.png)      

0. 用户程序调用MapReduce。
1. 用户程序中的MapReduce库将输入数据分成M片大小固定的片（每片大小16~64MB，可以由参数指定），然后启动集群中的程序拷贝。
2. 其中一个程序拷贝比较特殊，它就是master，其他都是执行master分配任务的worker。设有M个map任务和R个reduce任务。master挑选空闲的worker，分给它一个map或reduce任务。
3. 被分配map任务的worker读取对应的输入分片（split）文件。它从输入数据中解析出key/value对（第1类），并传给Map函数。Map输出的中间key/value对（第2类）缓存在内存中。    

**注意 ！第1类key/value和第2类key/value不一样。以wordcount为例，第1类key/value中key是文档名称，value是文档内容；第2类key/value中key是单词，value是单词出现次数。**

4. 缓存的中间key/value对周期性的写到本地磁盘，由分区函数分成R个区域。分区地址将被传给master，master负责将分区地址发送给reduce worker。
5. Master通知reduce work分区地址后，reduce work用RPC的方式从磁盘读取缓存数据。reduce work读完所有中间数据后，按中间key排序，所以相同的key值的数据将被分到一组。如果中间数据达到内存装不下，则用外排序。
6. reduce worker迭代读取排序后的中间数据，并将同一个key和其对应的value列表传给Reduce函数。Reduce函数的输出会追加写到这个reduce partition的最终输出文件，输出文件放到全区文件系统。
7. 当所有的map和reduce任务完成后，master唤醒用户程序，继续执行用户程序代码。

当所有都完成之后，mapreduce的输出在R个文件中（每个reduce任务一个文件）。通常不用将这R个文件合成1个文件，因为这R个文件可以作为下个MapReduce调用的输入。

## 容错   
### worker故障    
master会定期ping worker，如果很久没收到回应，则将该worker标记为故障。任何在此worker上完成的/进行中的map任务要置成调度前状态，供别的worker调度。因为map的结果存在本地磁盘，而master无法访问故障work，所以故障work上的map需要重新执行。而已经执行的reduce则不用再次执行，因为reduce将输出结果放到全局文件系统。map重新执行需要通知对应的reduce，以便reduce从正确的地方读取数据。
       
## master故障   
定期将master存下来，形成checkpoint。如果master故障，可以从checkpoint重启一个。如果只有一个master且master挂了，那么MapReduce任务终止，需要用户发现并重启。    

## 本地性    
网络带宽是分布式集群的稀缺资源。MapReduce任务的master拥有输入数据的位置，master总是在存有输入数据的机器上启动map，如果该机器故障，则启动同交换器下机器的map，这样可以减少网络传输。    

## 高级功能   
### 分区（Partitioning）函数     
MapRuduce用户指定Reduce任务的输出个数R，输出数据根据分区函数计算分区。默认的分区函数是`hash(key) mod R`其中key是中间key。有时需要别的分区函数，比如中间key是URL，希望同一主机上的条目在同一输出文件中。这种情况下，可选择`hash(Hostname(urlkey)) mod R`作为分区函数。    

### Combiner函数     
在数单词例子中，每个map都可能产生成千上百个`<the, 1>`记录，这些记录都通过网络传给同一个reduce，然后算出一个总的数量。MapReduce提供了更好的方法！通过Combiner函数先在本地计算，然后再传输到reduce，可以减少传输数据量。Combiner函数可以复用Reduce函数的代码，但Ruduce的输出写到最终输出文件，而combiner输出到中间文件。combiner函数大大加速了一些MapReduce操作。    

### 状态信息   
master节点运行HTTP服务，将很多状态页提供给用户。状态页显示计算进度，如多少任务已完成、多少还在进行、输入/中间/输出数据字节数、完成比例等。状态页还包含标准错误和输出数据的链接。用户可根据状态页预测还需要计算多久，是否需要添加计算资源等。用户可用状态页分析某阶段计算慢的原因。顶级状态页显示哪个worker失败，失败时运行的map和reduce任务，这些信息可用于定位用户代码中的bug。    

### 重新执行和网络带宽    
机器慢、机器故障和数据丢失都可以用重新执行解决。    
网络带宽是稀缺资源，所以需要本地优化，说白了就是尽量将能在本地执行的操作挪到本地。

*附wordcount完整程序：*     
	
	#include "mapreduce/mapreduce.h"

	// User’s map function
	class WordCounter : public Mapper {
	public:
	    virtual void Map(const MapInput &input) {
	        const string &text = input.value();
	        const int n = text.size();
	        for (int i = 0; i < n;) {
	            // Skip past leading whitespace
	            while ((i < n) && isspace(text[i]))
	                i++;

	            // Find word end
	            int start = i;
	            while ((i < n) && !isspace(text[i]))
	                i++;

	            if (start < i)
	                Emit(text.substr(start, i - start), "1");
	        }
	    }
	};

	REGISTER_MAPPER(WordCounter);

	// User’s reduce function
	class Adder : public Reducer {
	    virtual void Reduce(ReduceInput *input) {
			// Iterate over all entries with the
			// same key and add the values
	        int64 value = 0;
	        while (!input->done()) {
	            value += StringToInt(input->value());
	            input->NextValue();
	        }
	        // Emit sum for input->key()
	        Emit(IntToString(value));
	    }
	};

	REGISTER_REDUCER(Adder);

	int main(int argc, char **argv) {
	    ParseCommandLineFlags(argc, argv);

	    MapReduceSpecification spec;

		// Store list of input files into "spec" 
		for (int i = 1; i < argc; i++) {
		    MapReduceInput *input = spec.add_input();
		    input->set_format("text");
		    input->set_filepattern(argv[i]);
		    input->set_mapper_class("WordCounter");
		}

		// Specify the output files:
		// /gfs/test/freq-00000-of-00100
		// /gfs/test/freq-00001-of-00100
		// ...
		MapReduceOutput *out = spec.output();
		out->set_filebase("/gfs/test/freq");
		out->set_num_tasks(100); 
		out->set_format("text");
		out->set_reducer_class("Adder");

		// Optional: do partial sums within map 
		// tasks to save network bandwidth 
		out->set_combiner_class("Adder");

		// Tuning parameters: use at most 2000
		// machines and 100 MB of memory per task 
		spec.set_machines(2000);
		spec.set_map_megabytes(100);
		spec.set_reduce_megabytes(100);

		// Now run it
		MapReduceResult result;
		if (!MapReduce(spec, &result)) abort();

		// Done: ’result’ structure contains info 
		// about counters, time taken, number of 
		// machines used, etc.

		return 0;
	}


