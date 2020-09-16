Automatical WHU network authentication tool for OpenWrt
=
用于OpenWrt的武大校园网自动认证工具，理论上可以适用于其他使用锐捷ePortal方式认证的校园网络环境

如何使用？
--
1、安装依赖grep和curl，你的OpenWrt设备此时必须已经联网
````
opkg update
opkg install grep curl
````
2、断开你的SSH连接并重新连接，这是因为OpenWrt默认的grep和curl是BusyBox中的，默认的Shell ASH也是BusyBox中的，会话必须重启以保证独立的全功能grep和curl能被识别到

3、下载Release内的script-autowhu.tar.gz文件，上传到/tmp目录，然后运行以下命令解压：
````
cd /
##上一步为进入根目录，如果你已经在根目录了，则不需要
tar -xvzf /tmp/script-autowhu.tar
````
4、修改/etc/auto-whu.conf，将其中的username和pwd修改为你的账号和密码
5、执行auto-whu.sh来测试
````
auto-whu.sh
````
6、尝试到 http://user-serv.whu.edu.cn:8080/selfservice/ 断开当前路由器的连接，如果auto-whu.sh输出以下结果，则功能正常
````
WARNING: Check failed, offline, trying to reconnect
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   514  100   514    0     0  32125      0 --:--:-- --:--:-- --:--:-- 36714
INFO: (Re)connection successful
INFO: Still online, next check in 5 seconds
````