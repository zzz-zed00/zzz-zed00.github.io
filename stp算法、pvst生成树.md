# STP算法

STP将一个环形网络生成无环拓扑的步骤

第一步：选择根网桥

第二部；选择根端口

第三步：选择指端口

## 1.如何选择根网桥

根据网桥ID(BID)选择根网桥，谁的优先级小，谁就是网桥。如果优先级相同，谁的MAC地址小谁就是网桥。

BID：优先级+MAC地址

​	默认情况下交换机的优先级是：37768

​	查看交换机的MAC地址：switch#show version

​	base ethernetMAC Address：0001，967e，9162

## 2.选择根端口

#### (1) 如何选择根端口

在非根网桥上选择一个到根网桥最近的端口作为根端口，选择端口的依据是：

​	根路径的成本（cost值）从端口出发到根桥最低

​	直连网桥的网桥ID最小

​	直连网桥的端口ID最小

### (2)什么是cost值

根路径成本是网桥到根网桥的路径上所有链路的成本之和。

### (3)什么是端口ID

端口优先级(默认是128)+端口编号

## 3.选择指定端口

依据是

​	在每根网桥上选择一个指定端口，根桥上的端口全是指定端口。

非根桥上的指定端口：

​	根路径成本最低【从非根桥到根桥】

​	端口所在的网桥ID值较小

# pvst：按vlan生成树

## 1.划分vlan

## 2.设置sw1作为vlan10的根桥，sw2作为vlan10的备份根桥

sw1(config)#spanning-tree vlan 10 root primary

sw2(config)#spanning-tree vlan 10 root secondary

## 3.设置sw2作为vlan20的根桥，sw1作为vlan20的备份根桥

sw2(config)#spanning-tree vlan 20 root primary

sw1(config)#spanning-tree vlan 20 root secondary

# 配置端口聚合

sw1(config)#int port-channel 1  开启一个逻辑端口

sw1(config)#sw mo trunk

sw2(config)#int port-channel 1

sw2(config)#mo trunk

sw1(config)#int f0/4

sw1(config)#sw mo trunk

sw2(config)#int f0/4

sw2(config)#sw mo trunk

sw1(config)#int range f0/1,f0/4

sw1(config)#channel-group 1 mode on

sw2(config)#int range f0/1,f0/4

sw2(config)#channel-group 1 mode on

# 配置流量均衡

switch(config)#int f0/1

switch(config)#spanning-tree vlan 10 port-priority 16

switch(config)#spanning-tree vlan 20 port-priority 32

switch(config)#int f0/2

switch(config)#spanning-tree vlan 10 port-priority 32

switch(config)#spanning-tree vlan 20 port-priority 16

