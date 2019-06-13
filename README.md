一键脚本安装s-s/s-sR/V2-Ray + 开启bbr
---

一键脚本搭建s-s/s-sR/V2-Ray + 设置开启自启动 + 升级内核&开启bbr加速。

## 声明
本脚本源自于[flyzy小站]，目前已经被GFW拉入黑名单了，直接DNS污染了，国内无法访问。欢迎大家访问七彩blog(https://www.7colorblog.com)

## 支持系统
CentOS 6+

Debian 7+

Ubuntu 12+

## 使用教程
先安装git
Centos执行这个： `yum -y install git`<br>
Ubuntu/Debian执行这个： `apt-get update & apt-get -y install git`<br>

下载一键搭建ss脚本文件（直接在绿色光标处复制该行命令回车即可，只需要执行一次，卸载ss后也不需要重新下载）<br>
`git clone https://github.com/lizhongnian/ss-fly`<br>

运行搭建脚本搭建ss服务<br>
`ss-fly/ss-fly.sh -i 7colorblogcom 1024`<br>

上方命令的“7colorblog.com”是你ss的密码，可以为你自己常用密码，最后的数字为端口号，可以不填写，默认是1024，复制进shell回车执行即可，等待屏幕上弹出提示。<br>
注：如果需要改密码或者改端口，只需要重新再执行一次搭建ss脚本代码就可以了，或者修改/etc/shadowsocks.json这个配置文件。<br>

相关操作（到第三步就已经成功了，此步骤可以不看）<br>
启动：`/etc/init.d/ss-fly start`<br>
停止：`/etc/init.d/ss-fly stop`<br>
重启：`/etc/init.d/ss-fly restart`<br>
状态：`/etc/init.d/ss-fly status`<br>
修改配置文件：`vim /etc/shadowsocks.json`<br>


## 一键开启BBR加速
如果你觉得网速不够优秀，可以尝试开启BBR。<br>

BBR是Google开源的一套内核加速算法，可以让你搭建的shadowsocks/shadowsocksR速度上一个台阶，本一键搭建ss/ssr脚本支持一键升级最新版本的内核并开启BBR加速。<br>

BBR支持4.9以上的，如果低于这个版本则会自动下载最新内容版本的内核后开启BBR加速并重启，如果高于4.9以上则自动开启BBR加速，执行如下脚本命令即可自动开启BBR加速：<br>

`ss-fly/ss-fly.sh -bbr`<br>


装完后需要重启系统，输入y即可立即重启，或者之后输入reboot命令重启。等待一小会重新连接<br>

判断BBR加速有没有开启成功。输入以下命令：<br>
`sysctl net.ipv4.tcp_available_congestion_control`<br>
如果返回值为：<br>
net.ipv4.tcp_available_congestion_control = bbr cubic reno<br>

后面有bbr，则说明已经开启成功了。<br>



