##### 宝塔开源许可协议：https://www.bt.cn/kyxy.html
##### 使用手册：http://docs.bt.cn
##### 论坛地址：https://www.bt.cn/bbs
##### 反馈建议： https://www.bt.cn/bbs/forum-43-1.html
##### Bug提交：https://www.bt.cn/bbs/forum-39-1.html

#### 安装命令：
##### Centos
```bash
yum install -y wget && wget -O install.sh http://download.bt.cn/install/install_6.0.sh && sh install.sh
```
##### Ubuntu/Debian
```bash
wget -O install.sh http://download.bt.cn/install/install-ubuntu_6.0.sh && sudo bash install.sh
```

##### 宝塔面板关闭强制绑定账号教程

##### 作者： 柴郡猫

##### 2021年2月18日更新：

##### windows面板直接删除BtSoft\panel\data\bind_path.pl文件即可。（也可以将文件改名避免出错无法恢复）

##### linux面板还是采用20年1月30日更新的方式。

##### 2021年1月30日更新：

##### /www/server/panel/data/bind.pl删除这个文件即可。

##### 另外宝塔现在自带功能也可以关掉这个登录帐号限制。在SSH终端界面，输入bt进入宝塔常用操作选项界面，输入10，清除登陆限制即可。


##### 2020年9月29日更新：

##### 新装了一个机器的宝塔面板发现宝塔代码进行了简单的改动。下文中的if (bind_user == ‘True’) {现在在65行左右。

##### 使用同样的方式将True改为REMOVED即可。

##### 如果修改后没有生效，强制刷新页面即可。不会的就换个浏览器访问面板！

##### 下面说下怎么去掉这个弹窗。这里提供两种方式

##### 1.SSH修改
##### 在SSH内执行以下命令：
```bash
  sed -i "s|if (bind_user == 'True') {|if (bind_user == 'REMOVED') {|g" /www/server/panel/BTPanel/static/js/index.js
```
##### 执行以上命令就可以了。如果要恢复可以执行下面的命令
```bash
  sed -i "s|if (bind_user == 'REMOVED') {|if (bind_user == 'True') {|g" /www/server/panel/BTPanel/static/js/index.js
```
##### 如果修改后没有生效，强制刷新页面即可。不会的就换个浏览器访问面板！

##### 2.在面板里修改弹窗的代码
##### 进入宝塔后修改宝塔地址，进入files文件管理界面。http://你的IP地址:8888/files


##### 找到文件/www/server/panel/BTPanel/static/js/index.js

##### 打开编辑，就在第一行有个if (bind_user == ‘True’) {

##### 将True改为REMOVED即可。

##### 如果修改后没有生效，强制刷新页面即可。不会的就换个浏览器访问面板！



