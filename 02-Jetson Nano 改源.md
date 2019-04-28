Jetson Nano 改源
---
在ubuntu系统中，有一个文件，里面放着更新源信息，当我们下载软件的时候，都会去文件里找去哪个服务器下载。但是系统是国外的，更新源默认都是外国服务器，我们下载软件自然很吃力，因此我们将源换成国内的。

#### 1.系统类型
```shell
dnano@dnano-desktop:~$ uname  -a
Linux dnano-desktop 4.9.140-tegra #1 SMP PREEMPT Wed Mar 13 00:32:22 PDT 2019 aarch64 aarch64 aarch64 GNU/Linux
```
一定要注意处理器是**aarch64**类型的，**更要使用与之匹配的源** ，**切记！**   
最开始的时候，我直接修改source.list，因为没有注意aarch64，导致安装错误、失败等各种问题...  
___
*想要了解aarch64和arm64的区别*  
详情查看网址[What is the difference between different implemetation of arm64/aarch64 for Linux or other software to run on? [closed]
](https://unix.stackexchange.com/questions/461179/what-is-the-difference-between-different-implemetation-of-arm64-aarch64-for-linu)  
简要描述：  

>*AArch64 is the 64-bit state introduced in the Armv8-A architecture. The 32-bit state which is backwards compatible with Armv7-A and previous 32-bit Arm architectures is referred to as AArch32. Therefore the GNU triplet for the 64-bit ISA is aarch64. The Linux kernel community chose to call their port of the kernel to this architecture arm64 rather than aarch64, so that's where some of the arm64 usage comes from.*
*As far as I know the Apple backend for aarch64 was called arm64 whereas the LLVM community-developed backend was called aarch64 (as it is the canonical name for the 64-bit ISA) and later the two were merged and the backend now is called aarch64.*
*So aarch64 and arm64 refer to the same thing.*
___
#### 2.修改source.list文件
在路径```/etc/apt/```下有```source.list```文件，  
（1）对该文件进行复制备份；  
```shell
dnano@dnano-desktop:/etc/apt$ sudo cp sources.list sources.list.bak
```
（2）使用```vim或者gedit```等工具对```source.list```文件进行编辑；  

直接清空source.list文件内容，根据个人喜好选择下述中科大或者清华的arm64源，粘进文件，保存。
___
*中科大*
>deb http://mirrors.ustc.edu.cn/ubuntu-ports/ xenial-backports main multiverse restricted universe
deb http://mirrors.ustc.edu.cn/ubuntu-ports/ xenial-proposed main multiverse restricted universe
deb http://mirrors.ustc.edu.cn/ubuntu-ports/ xenial-security main multiverse restricted universe
deb http://mirrors.ustc.edu.cn/ubuntu-ports/ xenial-updates main multiverse restricted universe
deb-src http://mirrors.ustc.edu.cn/ubuntu-ports/ xenial main multiverse restricted universe
deb-src http://mirrors.ustc.edu.cn/ubuntu-ports/ xenial-backports main multiverse restricted universe
deb-src http://mirrors.ustc.edu.cn/ubuntu-ports/ xenial-proposed main multiverse restricted universe
deb-src http://mirrors.ustc.edu.cn/ubuntu-ports/ xenial-security main multiverse restricted universe
deb-src http://mirrors.ustc.edu.cn/ubuntu-ports/ xenial-updates main multiverse restricted universe

*清华*
>deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports/ xenial main multiverse restricted universe
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports/ xenial-security main multiverse restricted universe
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports/ xenial-updates main multiverse restricted universe
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports/ xenial-backports main multiverse restricted universe
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports/ xenial main multiverse restricted universe
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports/ xenial-security main multiverse restricted universe
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports/ xenial-updates main multiverse restricted universe
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports/ xenial-backports main multiverse restricted universe
___
#### 3.更新
```shell
dnano@dnano-desktop:~$ sudo apt-get update

'''如有需要，执行下述命令对文件进行升级'''
dnano@dnano-desktop:~$ sudo apt-get upgrade
```
至此，完成系统更改源的操作，接下来就是**配置整个系统**的过程了。
