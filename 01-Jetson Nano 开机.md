Jetson Nano 开机
---
从某宝入手了一台Jetson Nano（899大洋，送电源和16G内存卡），开始了一路采坑的经历......遂整理了这些过程。

本文介绍如何首次开启系统，主要参考[官网介绍](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit)，很是顺利。
#### 1.产品介绍
Nvidia JEtson Nano Developer Kit是一款可供大家用来制作、学习、开发使用的小型AI计算机，通过简明的教程，我们可以开发AI应用、超酷的AI机器人等其他更有趣的项目。

购买的话，仅有一台裸机，需自行购买内存卡、键鼠、5V2A直流电源、显示器（无线网卡、摄像头等设备视情况购买）等设备。
![产品外观](https://img-blog.csdnimg.cn/201904281907141.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTM2MTcyMjk=,size_16,color_FFFFFF,t_70)
（1）内存卡（microSD card）  
（2）40针扩展插针  
（3）Micro-USB 5V电源接口  
（4）网孔  
（5）4个USB3.0插口  
（6）HDMI接口  
（7）DP接口  
（8）直流Barrel Jack 5Vd电源接口  
（9）MIPI CSI摄像头接口  
#### 2.写入系统镜像
拿到自己的microSD卡后（大点还是有必要的，本人某东上购买```64G U3 C10 A2 V30 4K```）；    
（1）官网下载[系统镜像](https://developer.nvidia.com/embedded/dlc/jetson-nano-dev-kit-sd-card-image)（Ubuntu 18.04LTS）；  
（2）下载镜像制作工具[Etcher](https://www.balena.io/etcher)；  
（3）傻瓜式操作，选择插入的microSD卡，然后点击“Flash!”，直到制作完成。  
![Etcher操作](https://img-blog.csdnimg.cn/20190428192251304.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTM2MTcyMjk=,size_16,color_FFFFFF,t_70)
#### 3.首次启动和设置
直接粘贴官网动图，非常直观；  
![接线](https://img-blog.csdnimg.cn/20190428192655398.gif)  
内存卡插在如下图的位置；  
![内存卡位置](https://img-blog.csdnimg.cn/2019042819275424.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTM2MTcyMjk=,size_16,color_FFFFFF,t_70)
按下电源后，电路板上绿色的电源指示灯会亮起。首次启动，需要配置系统：  
（1）阅读和接受Nvidia Jetson Nano的软件EULA；  
（2）选择系统语言（根据个人习惯，我选了中文）、键盘风格、时区；  
（3）创建用户名、密码；  
（4）我使用的是某米的无线网卡，无需配置，即插即用，成功连接wifi。  

系统启动后，界面如下，首次开机会有个简要的介绍。
![系统界面](https://img-blog.csdnimg.cn/20190428193320457.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTM2MTcyMjk=,size_16,color_FFFFFF,t_70)
至此，系统已经安装完成，可以正常开启，**但，坑才刚刚开始......**
