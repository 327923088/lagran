- 本小程序主要用来实现Geneva的以下四条规则，还可以自定义端口、需要修改的window size的值。
```
"[TCP:flags:SA]-tamper{TCP:window:replace:0}-|"
"[TCP:flags:A]-tamper{TCP:window:replace:0}-|"
"[TCP:flags:PA]-tamper{TCP:window:replace:0}-|"
"[TCP:flags:FA]-tamper{TCP:window:replace:0}-|"
```
- 默认四条规则全部开启，具体使用方法参考`./lagran -h`。
- 例如：开启第一条规则并设置window为2，同时关闭2、3、4条规则
```./lagran -debug -p 80 -sa=true -wsa 2 -a=false -pa=false -fa=false```
- 注意：本小程序依赖libpcap-dev、libnetfilter-queue-dev、iptables等使用之前请先安装。

yum install lrzsz -y

yum install libpcap-devel libnetfilter* -y

./lagran -p 80,443 -sa=true -wsa 4 -a=false -pa=false -fa=false -daemon -forever

查看运行状态
iptables -nvL

关闭
iptables -L OUTPUT --line-numbers -nv
sudo iptables -D OUTPUT 1
让好kill掉lagran进程

下载
wget https://raw.githubusercontent.com/327923088/lagran/master/lagran
