# OpenVPN-Access-Server
openvpn 快速搭建
Centos7 OpenVPN Access Server 安装（最新版+破解多用户限制）

参考网址：
https://www.wangfeng.live/2020/11/centos7-openvpn-access-server-installation-latest-version/

破解版安装包git网址：
https://gitee.com/wangfeng-1/openvpnas

https://github.com/heroking/openvpn_as_crack

安装OpenVPN Access Server
网络允许：：建议安装OpenVPN Access Server的方法是使用官方的OpenVPN Access Server软件存储库。安装OpenVPN Access Server客户端安装包和OpenVPN Access Server软件包本身。

yum -y install https://as-repository.openvpn.net/as-repo-centos7.rpm
yum -y install openvpn-as

网络不允许：如果由于某种原因无法通过官方的软件存储库安装，可以将软件包下载下来后上传到服务器进行安装。

rpm -ivh openvpn-as-2.5.2-CentOSrelease.x86_64.rpm
![image](https://user-images.githubusercontent.com/50575594/115898439-9ea67900-a46e-11eb-96d5-ba2fae65bc29.png)


安装完成后修改管理密码：

passwd openvpn
![image](https://user-images.githubusercontent.com/50575594/115898222-5be4a100-a46e-11eb-9915-21b12c294047.png)


管理端Admin UI: https://192.168.1.10/admin

登录后可以看到最多允许两个用户连接，个人使用足够了，不够的话下面有破解方法。
![image](https://user-images.githubusercontent.com/50575594/115898274-6bfc8080-a46e-11eb-988d-86d3ccfc31bd.png)


客户端Client UI: https://192.168.1.10:943/
![image](https://user-images.githubusercontent.com/50575594/115898514-b251df80-a46e-11eb-8276-8708e27fb6f4.png)


破解多用户限制
1、首先下载破解文件：pyovpn-2.0-py2.7.egg
![image](https://user-images.githubusercontent.com/50575594/115898574-c3025580-a46e-11eb-9968-76bda090f927.png)

2、将破解文件放到/usr/local/openvpn_as/lib/python2.7/site-packages/目录下，备份或者覆盖之前文件。

cp pyovpn-2.0-py2.7.egg /usr/local/openvpn_as/lib/python2.7/site-packages/
![image](https://user-images.githubusercontent.com/50575594/115898632-d44b6200-a46e-11eb-9b3d-580a0c46e205.png)

3、执行初始化操作

进入/usr/local/openvpn_as/bin目录中

cd /usr/local/openvpn_as/bin
![image](https://user-images.githubusercontent.com/50575594/115898687-e3321480-a46e-11eb-8cfe-a17aa6a8a132.png)

直接执行./_ovpn-init

./ovpn-init
如报错找不到相关模块，编辑_ovpn-init 注解掉即可。
![image](https://user-images.githubusercontent.com/50575594/115898717-ecbb7c80-a46e-11eb-8ac7-f74626c8d7f2.png)


然后再次执行初始化脚本
![image](https://user-images.githubusercontent.com/50575594/115898750-f3e28a80-a46e-11eb-9c44-988a1dd55394.png)

![image](https://user-images.githubusercontent.com/50575594/115898779-fba22f00-a46e-11eb-8ead-c77fa7553945.png)

然后一路回车即可，等待初始化配置完成。
![image](https://user-images.githubusercontent.com/50575594/115898805-02c93d00-a46f-11eb-8333-b6995d3271f8.png)


重新登录控制台，查看1024 个。
![image](https://user-images.githubusercontent.com/50575594/115898821-0a88e180-a46f-11eb-9afd-4c248f7b79f3.png)

