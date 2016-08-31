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
	
