


异常No Spring WebApplicationInitializer types detected on classpath    
该异常好像不影响页面访问，所以先搁置处理。


2016-09-12 11:31:05.109:INFO:/:No Spring WebApplicationInitializer types detected on classpath
2016-09-12 11:31:05.797:INFO:/:Initializing Spring root WebApplicationContext
Failed to connect 10.4.232.70:4252
org.apache.thrift.transport.TTransportException: java.net.SocketTimeoutException: Read timed out
	at org.apache.thrift.transport.TIOStreamTransport.read(TIOStreamTransport.java:129)
	at org.apache.thrift.transport.TTransport.readAll(TTransport.java:84)
	at org.apache.thrift.transport.TFramedTransport.readFrame(TFramedTransport.java:129)
	at org.apache.thrift.transport.TFramedTransport.read(TFramedTransport.java:101)
	at org.apache.thrift.transport.TTransport.readAll(TTransport.java:84)
	at org.apache.thrift.protocol.TBinaryProtocol.readAll(TBinaryProtocol.java:378)
	at org.apache.thrift.protocol.TBinaryProtocol.readI32(TBinaryProtocol.java:297)
	at org.apache.thrift.protocol.TBinaryProtocol.readMessageBegin(TBinaryProtocol.java:204)
	at org.apache.thrift.TServiceClient.receiveBase(TServiceClient.java:69)
	at com.meituan.scribe.thrift.MTLog$Client.recv_Log(MTLog.java:80)
	at com.meituan.scribe.thrift.MTLog$Client.Log(MTLog.java:67)
	at org.apache.logging.log4j.scribe.appender.ScribeAppender.sendLogEntry(ScribeAppender.java:312)
	at org.apache.logging.log4j.scribe.appender.ScribeAppender.access$300(ScribeAppender.java:55)
	at org.apache.logging.log4j.scribe.appender.ScribeAppender$FlushLogEntry.run(ScribeAppender.java:365)
	at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:471)
	at java.util.concurrent.FutureTask.runAndReset(FutureTask.java:304)
	at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.access$301(ScheduledThreadPoolExecutor.java:178)
	at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.run(ScheduledThreadPoolExecutor.java:293)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1145)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:615)
	at java.lang.Thread.run(Thread.java:745)
Caused by: java.net.SocketTimeoutException: Read timed out
	at java.net.SocketInputStream.socketRead0(Native Method)
	at java.net.SocketInputStream.read(SocketInputStream.java:152)
	at java.net.SocketInputStream.read(SocketInputStream.java:122)
	at java.io.BufferedInputStream.fill(BufferedInputStream.java:235)
	at java.io.BufferedInputStream.read1(BufferedInputStream.java:275)
	at java.io.BufferedInputStream.read(BufferedInputStream.java:334)
	at org.apache.thrift.transport.TIOStreamTransport.read(TIOStreamTransport.java:127)
	... 20 more
2016-09-12 11:31:09.911:INFO:/:Initializing Spring FrameworkServlet 'mvc-dispatcher'
2016-09-12 11:31:10.753:INFO:oejs.NCSARequestLog:Opened /Users/linxuan/IdeaProjects/edlp/edlp-web/logs/jetty.request.log.2016-09-12
2016-09-12 11:31:10.760:INFO:oejs.AbstractConnector:Started SelectChannelConnector@0.0.0.0:8080