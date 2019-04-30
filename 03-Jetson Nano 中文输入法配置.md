Jetson Nano配置与使用（3）中文输入法ibus
---
由于经常使用到中文搜索，所以安装了中文输入法，Jetson Nano自带ibus中文输入法，但是要简单的配置下才能进行中文的输入。

#### 1.安装文件 ibus-pinyin
ibus是直接安装了，直接输入```ibus```会显示如下内容；
```shell
dnano@dnano-desktop:~$ ibus
用法：ibus 命令 [选项...]

命令：
  engine          设定或获取引擎
  exit            退出 ibus-daemon
  list-engine     显示可用引擎
  watch           (暂不可用)
  restart         重启 ibus-daemon
  version         显示版本号
  read-cache      显示注册缓存内容。
  write-cache     创建注册缓存
  address         输出 ibus-daemon 位于 D-Bus 中的地址
  read-config     显示配置值
  reset-config    重置配置
  emoji           将面板中的 emoji 保存到剪贴板 
  help            显示本信息
```
安装```ibus-pinyin```
```shell
sudo apt-get install ibus-pinyin
```
#### 2. 系统设置
在系统设置中，双击"**language support**"；  
![language support](https://img-blog.csdnimg.cn/20190428204654530.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTM2MTcyMjk=,size_16,color_FFFFFF,t_70)  
点击“**install / remove language...**”，选择**简体中文**，输入密码，此时系统会进行更新，大约几分钟，安装过程如下；
![选择安装的语言包](https://img-blog.csdnimg.cn/20190428205124918.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTM2MTcyMjk=,size_16,color_FFFFFF,t_70)  
![安装过程](https://img-blog.csdnimg.cn/20190428204946721.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTM2MTcyMjk=,size_16,color_FFFFFF,t_70)  
将**汉语（中国）**拖到最上端；  
![拖拽汉语放入首位](https://img-blog.csdnimg.cn/20190428205318177.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTM2MTcyMjk=,size_16,color_FFFFFF,t_70)  
点击**Apply System-Wide**，并将**keyboard input method system**下拉选框选到**ibus**；  
![设置apply system wide](https://img-blog.csdnimg.cn/20190428205543340.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTM2MTcyMjk=,size_16,color_FFFFFF,t_70)  
#### 3.ibus设置
终端下输入
```shell
dnano@dnano-desktop:~$ ibus-setup
```
弹出如下画面，切换到**输入法**选项卡，点击**添加**按钮，选择**汉语**，有两个选项，选择**Pinyin**；
![ibus配置](https://img-blog.csdnimg.cn/20190428205622206.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTM2MTcyMjk=,size_16,color_FFFFFF,t_70)  
输入下述命令，重新启动ibus
```shell
dnano@dnano-desktop:~$ ibus restart
```
#### 4. 重启电脑
键入reboot命令，重新启动Jetson Nano，在终端下测试，已经可以输入中文。
