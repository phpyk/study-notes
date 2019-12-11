# ifconfig和ip addr命令

Linux查看IP的命令除了ifconfig，还可以用ip addr命令
```
[root@iZwz9ax55uy1w0vrqsr6fiZ go]# ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:16:3e:0e:67:a0 brd ff:ff:ff:ff:ff:ff
    inet 172.18.161.137/20 brd 172.18.175.255 scope global dynamic eth0
       valid_lft 315259321sec preferred_lft 315259321sec
```

inet (ip地址)：172.18.161.137/20
brd （广播地址）：172.18.175.255
link/ether（MAC地址）：00:16:3e:0e:67:a0
lo 全称是 loopback，又称环回接口，往往会被分配到 127.0.0.1 这个地址

> ifconfig和ip addr命令的区别：  
> 1. 需要安装的工具不同，一个是net-tools,一个是iproute2  
> 2. ip addr 不显示子网掩码  

### 网络设备的状态标识：
<BROADCAST,MULTICAST,UP,LOWER_UP>
* BROADCAST 表示这个网卡有广播地址，可以发送广播包
* MULTICAST 表示网卡可以发送多播包
* UP 表示网卡处于启动的状态
* LOWER_UP 表示 L1 是启动的，也即网线插着呢

mtu 1500 表示最大传输单元 MTU 为 1500，这是以太网的默认值。
qdisc pfifo_fast 表示排队规则为：pfifo_fast 先进先出