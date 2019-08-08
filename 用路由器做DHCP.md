# 用路由器做DHCP

<!--more-->

R1(config)# ip dhcp pool vlan100   配置地址池名称

R1(dhcp-config)#network  192.168.100.0 255.255.255.0   分配地址范围

R1(dhcp-config)#default-router  192.168.100.254   分配的网关地址

R1(dhcp-config)#dns-server 61.139.2.69

R1(config)#ip dhcp excluded-address 192.168.1 192.168.1.10  排除地址

# DHCP中继

## 1.配置dhcp服务器

## 2.在网关接口上配置转发

switch(config)#int  vlan 10

ip(config-if)#helper-address 192.168.30.1

## 3.pc端

pc>ipconfig /release

pc>ipconfig /renew

pc>ipconfig /all

