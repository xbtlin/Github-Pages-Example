---
layout:     post
title:      Tensorflow安装和示例
category: blog
description: Tensorflow安装和示例
---

## 通过Pip安装Tensorflow   
Pip是Python包管理系统。      
安装pip: 
	
	# Ubuntu/Linux 64-bit
	$ sudo apt-get install python-pip python-dev

	# Mac OS X
	$ sudo easy_install pip
	$ sudo easy_install --upgrade six   
	
然后选择合适的二进制文件： 

	# Ubuntu/Linux 64-bit, CPU only, Python 2.7
	$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.10.0rc0-cp27-none-linux_x86_64.whl

	# Ubuntu/Linux 64-bit, GPU enabled, Python 2.7
	# Requires CUDA toolkit 7.5 and CuDNN v4. For other versions, see "Install from sources" below.
	$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.10.0rc0-cp27-none-linux_x86_64.whl

	# Mac OS X, CPU only, Python 2.7:
	$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/mac/cpu/tensorflow-0.10.0rc0-py2-none-any.whl

	# Mac OS X, GPU enabled, Python 2.7:
	$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/mac/gpu/tensorflow-0.10.0rc0-py2-none-any.whl

	# Ubuntu/Linux 64-bit, CPU only, Python 3.4
	$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.10.0rc0-cp34-cp34m-linux_x86_64.whl

	# Ubuntu/Linux 64-bit, GPU enabled, Python 3.4
	# Requires CUDA toolkit 7.5 and CuDNN v4. For other versions, see "Install from sources" below.
	$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.10.0rc0-cp34-cp34m-linux_x86_64.whl

	# Ubuntu/Linux 64-bit, CPU only, Python 3.5
	$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.10.0rc0-cp35-cp35m-linux_x86_64.whl

	# Ubuntu/Linux 64-bit, GPU enabled, Python 3.5
	# Requires CUDA toolkit 7.5 and CuDNN v4. For other versions, see "Install from sources" below.
	$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.10.0rc0-cp35-cp35m-linux_x86_64.whl

	# Mac OS X, CPU only, Python 3.4 or 3.5:
	$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/mac/cpu/tensorflow-0.10.0rc0-py3-none-any.whl

	# Mac OS X, GPU enabled, Python 3.4 or 3.5:
	$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/mac/gpu/tensorflow-0.10.0rc0-py3-none-any.whl     
	
如果你的电脑是OSX El Capitan系统，在Upgrading setuptools时会报Error。解决办法是在命令后面加`--user python`    

	pip install --upgrade setuptools --user python

这个问题来自[tensorflow网站](https://www.tensorflow.org/versions/r0.10/get_started/os_setup.html#common-problems)的另一个解释：On El Capitan, "six" is a special package that can't be modified, and this error is reported when "pip install" tried to modify this package. To fix use "ignore-installed" flag, ie

	sudo pip install --ignore-installed six https://storage.googleapis.com/....
	
安装成功返回：    
	
	...
	Successfully installed numpy-1.8.0rc1 protobuf-3.0.0b2 setuptools-1.1.6 tensorflow-0.10.0rc0 wheel-0.29.0   
	

import tensorflow遇到错误：

	>>> import tensorflow
	RuntimeError: module compiled against API version 0xa but this version of numpy is 0x9
	Traceback (most recent call last):
	  File "<stdin>", line 1, in <module>
	  File "/Users/linxuan/Library/Python/2.7/lib/python/site-packages/tensorflow/__init__.py", line 23, in <module>
	    from tensorflow.python import *
	  File "/Users/linxuan/Library/Python/2.7/lib/python/site-packages/tensorflow/python/__init__.py", line 48, in <module>
	    from tensorflow.python import pywrap_tensorflow
	  File "/Users/linxuan/Library/Python/2.7/lib/python/site-packages/tensorflow/python/pywrap_tensorflow.py", line 28, in <module>
	    _pywrap_tensorflow = swig_import_helper()
	  File "/Users/linxuan/Library/Python/2.7/lib/python/site-packages/tensorflow/python/pywrap_tensorflow.py", line 24, in swig_import_helper
	    _mod = imp.load_module('_pywrap_tensorflow', fp, pathname, description)
	ImportError: numpy.core.multiarray failed to import	
原因是系统中安装了多个numpy，而默认的那个版本太低。找到默认numpy的版本：     

	import numpy
	print numpy.__path__   

对我来说是`/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/numpy`。将这个numpy文件夹改名成numpy_old就解决问题了。
