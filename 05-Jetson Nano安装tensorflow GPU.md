Jetson Nano配置与使用（5）cuda测试及tensorflow gpu安装
---
Jetson Nano利用官方镜像进行安装后，系统已经安装好了JetPack，cuda，cudaa，OpenCV等组件，不过需要修改下环境变量才可以使用。

#### 1.修改环境变量
利用vim打开 ~ 路径下.bashrc文件：
```shell
sudo vi ~./bashrc
```
文件的最后添加以下三行：
```shell
export PATH=/usr/local/cuda-10.0/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH
export CUDA_HOME=$CUDA_HOME:/usr/local/cuda-10.0
```
重新执行.bashrc文件，直接生效；
```shell
source ~./bashrc
```
输入**nvcc -V**命令进行测试，如果显示如下信息，证明修改正确。
```shell
dnano@dnano-desktop:~$ nvcc -V
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2018 NVIDIA Corporation
Built on Sun_Sep_30_21:09:22_CDT_2018
Cuda compilation tools, release 10.0, V10.0.166
```
#### 2.测试cuda
官方镜像安装的系统中自带了一些案例，利用已有的案例进行测试。
```shell
cd /usr/src/cudnn_samples_v7/mnistCUDNN
sudo make
sudo chmod a+x mnistCUDNN
./mnistCUDNN
```
执行完上述命令，如果最后出现==Test passed!== 证明验证成功。
#### 3.安装pip3
```shell
sudo apt-get install python3-pip python3-dev
```
但是使用过程中，会发现报不能导入'main'错误，
```shell
dnano@dnano-desktop:~$ sudo pip3 install sklearn
Traceback (most recent call last):
  File "/usr/bin/pip3", line 9, in <module>
    from pip import main
ImportError: cannot import name 'main'
```
打开路径 "/usr/bin/"下的pip3文件，
将内容
```python3
from pip import main
if __name__ == '__main__':
    sys.exit(main())
```
修改为： 
```python3
from pip import __main__
if __name__ == '__main__':
    sys.exit(__main__._main())
```
#### 4.安装GPU版tensorflow
（1）安装一些依赖
```shell
sudo apt-get install libhdf5-serial-dev hdf5-tools
```
（2）安装GPU版本的tensorflow
```shell
pip3 install --extra-index-url https://developer.download.nvidia.com/compute/redist/jp/v42 tensorflow-gpu==1.13.1+nv19.3 --user
```
（3）tensorflow测试

找些测试代码即可，这里用gpu计算常数加法的小例子进行测试。
```python3
import tensorflow as tf
 
with tf.device('/cpu:0'):
    a = tf.constant([1.0,2.0,3.0],shape=[3],name='a')
    b = tf.constant([1.0,2.0,3.0],shape=[3],name='b')
with tf.device('/gpu:1'):
    c = a+b
   
sess = tf.Session(config=tf.ConfigProto(allow_soft_placement=True,log_device_placement=True))
sess.run(tf.global_variables_initializer())
print(sess.run(c))
```
#### 5.安装机器学习常用的python库
```shell
sudo apt-get install python3-numpy
sudo apt-get install python3-scipy
sudo apt-get install python3-pandas
sudo apt-get install python3-matplotlib
sudo apt-get install python3-sklearn
```
环境基本搭建完成。
