Jetson Nano配置与使用（6）Xshell6下caffe安装
---
安装caffe前需要做些准备工作，而且整个过程也比较久，中间有可能会出现各种问题，务必要仔细认真一步一步操作。首先参照之前的文章，使用Xshell6连接好Jetson Nano，然后开始以下内容。
#### 1.修改hosts文件
由于是本地编译安装，使用到了```git clone```命令，正常情况下，速度慢的可怜，在没有梯子的情况下，只能修改下hosts文件来自我安慰了，相比原来，速度也是提升了不少，此处留下了激动的泪水。废话少说，干！
（1）找到本地的hosts文件，并打开，
```shell
dnano@dnano-desktop:~$ sudo vi /etc/hosts
```
（2）在文件的末尾添加以下内容，顺便将 ```ports.ubuntu.com```也添加了,
```shell 
 192.30.255.112 https://github.com
 192.30.255.113 https://github.com
 151.101.76.249 github.global.ssl.fastly.net
 91.189.88.151 ports.ubuntu.com
 91.189.88.150 ports.ubuntu.com
```
（3）重启网络，生效修改后的hosts文件，
```shell
dnano@dnano-desktop:~$ sudo /etc/init.d/networking restart
```
#### 2.安装依赖
```shell
sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler
 
sudo apt-get install --no-install-recommends libboost-all-dev
 
sudo apt-get install libopenblas-dev liblapack-dev libatlas-base-dev
 
sudo apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev
 
sudo apt-get install git cmake build-essential
```
#### 3.安装caffe
（1）使用```git```将源码克隆到本地，时间视网速情况，
```shell
git clone https://github.com/BVLC/caffe.git
```
（2）根据caffe提供的示例文件```Makefile.config.example```生成```Makefile.config```,
```shell
cd caffe
sudo cp Makefile.config.example Makefile.config
```
（3）修改```Makefile.config```文件，
```python3
【1】将以下内容前的注释符号去掉，分别位于第5行、23行、92行；
5 USE_CUDNN := 1
23 OPENCV_VERSION := 3
9 WITH_PYTHON_LAYER := 1

【2】将第39行 CUDA_ARCH中的20、21内容去掉；
 39 CUDA_ARCH := -gencode arch=compute_30,code=sm_30 \
 40                 -gencode arch=compute_35,code=sm_35 \
 41                 -gencode arch=compute_50,code=sm_50 \
 42                 -gencode arch=compute_52,code=sm_52 \
 43                 -gencode arch=compute_60,code=sm_60 \
 44                 -gencode arch=compute_61,code=sm_61 \
 45                 -gencode arch=compute_61,code=compute_61

【3】将95、96行修改为以下内容；
95 INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include /usr/include/hdf5/serial
96 LIBRARY_DIRS := $(PYTHON_LIB) /usr/local/lib /usr/lib /usr/lib/aarch64-linux-gnu /usr/lib/aarch64-linux-gnu/hdf5/serial
```
（4）修改```Makefile```文件，
```python3
【1】修改第181行为以下内容；
LIBRARIES += glog gflags protobuf boost_system boost_filesystem m hdf5_serial_hl hdf5_serial

【2】修改第425行为以下内容；
NVCCFLAGS += -D_FORCE_INLINES -ccbin=$(CXX) -Xcompiler -fPIC $(COMMON_FLAGS)
```
（5）编译，时间比较久，看集美剧，静候美好结局，哈哈哈...
```shell
dnano@dnano-desktop:~/caffe$ sudo make
```
#### 4.测试
终于编译完了， ==从caffe文件夹返回到上一层，再打开python3==，输入```import caffe```，不发生错误，说明安装成功。
```python3
dnano@dnano-desktop:~$ python3
Python 3.6.7 (default, Oct 22 2018, 11:32:17) 
[GCC 8.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import caffe
>>> caffe.__
caffe.__class__(          caffe.__lt__(
caffe.__delattr__(        caffe.__name__
caffe.__dict__            caffe.__ne__(
caffe.__dir__(            caffe.__new__(
caffe.__doc__             caffe.__package__
caffe.__eq__(             caffe.__path__
caffe.__format__(         caffe.__reduce__(
caffe.__ge__(             caffe.__reduce_ex__(
caffe.__getattribute__(   caffe.__repr__(
caffe.__gt__(             caffe.__setattr__(
caffe.__hash__(           caffe.__sizeof__(
caffe.__init__(           caffe.__spec__
caffe.__init_subclass__(  caffe.__str__(
caffe.__le__(             caffe.__subclasshook__(
caffe.__loader__
```
