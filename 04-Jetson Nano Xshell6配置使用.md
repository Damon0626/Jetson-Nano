Jetson Nano配置与使用（4）win环境下使用Xshell6登录Jetson Nano
---
使用两套键盘、鼠标、显示器，个人觉得太麻烦。使用Xshell6，一来可以节省Jetson Nano很多内存，二来操作起来很是方便，搭配Xftp6和Xmanager6使用，完全够用。

#### 1.软件下载
Xshell6商用版是收费的， **家庭和学校用户版**是免费的，虽然免费版功能有限制，但是足够我们目前使用，详细信息可以在网址[https://www.netsarang.com/zh/free-for-home-school/](https://www.netsarang.com/zh/free-for-home-school/)中查看。
![填写信息界面](https://img-blog.csdnimg.cn/20190430211536753.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTM2MTcyMjk=,size_16,color_FFFFFF,t_70)
填写**姓名**和**邮件**，建议Xshell和Xftp两者都选，文件传递是要用得到Xftp的。填写好信息，你将会收到一封含有**下载地址**的邮件，直接点击进行下载安装。
#### 2.Xmanager6的安装
matplotlib、OpenCV等库可能会用到显示图形、图像等功能，根据需要还是安装了Xmanager6，官网收费。国内某下载网站有破解版本，下载使用即可。  
![Xmanager6](https://img-blog.csdnimg.cn/20190430212445883.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTM2MTcyMjk=,size_16,color_FFFFFF,t_70)
#### 3.软件配置
只要配置Xshell6即可：
（1）"文件"==>"新建会话属性"，点击左侧菜单树中"连接"，填写名称、主机等信息；

>名称：（用户随意）  
>主机：（Jetson Nano机子的IP地址）  
>协议：SSH  
>端口号：22  

![名称和IP信息配置](https://img-blog.csdnimg.cn/20190430212901304.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTM2MTcyMjk=,size_16,color_FFFFFF,t_70)  
（2）点击左侧菜单树中"用户身份验证"，填写用户名和密码。
>用户名/密码：（Jetson Nano用户设置的登录账号和密码）
>
![用户名密码配置](https://img-blog.csdnimg.cn/20190430213657684.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTM2MTcyMjk=,size_16,color_FFFFFF,t_70)  
#### 4.连接及使用
Xshell6配置完成后，点击连接按钮，就可以连上Jetson Nano了，连接成功，显示如下，以后都将在这个窗口里对Jetson Nano系统进行操作和使用。
```shell
Xshell 6 (Build 0121)
Copyright (c) 2002 NetSarang Computer, Inc. All rights reserved.

Type `help' to learn how to use Xshell prompt.
[C:\~]$ 

Connecting to 192.168.1.105:22...
Connection established.
To escape to local shell, press 'Ctrl+Alt+]'.

Welcome to Ubuntu 18.04.2 LTS (GNU/Linux 4.9.140-tegra aarch64)

Last login: Tue Apr 30 19:44:26 2019 from 192.168.1.104
dnano@dnano-desktop:~$ 
```
如需使用Xftp6可以直接点击菜单栏中的"新建文件传输按钮"，如下。
  
![Xftp6菜单栏](https://img-blog.csdnimg.cn/20190430214448939.png)  
  
Xftp6连接成功后，在如下界面中，可以实现双击和拖拽等方式的传输操作。
  
![Xftp6](https://img-blog.csdnimg.cn/20190430214639518.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTM2MTcyMjk=,size_16,color_FFFFFF,t_70)  
