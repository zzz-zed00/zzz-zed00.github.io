# nmap

## nmap的功能

·扫描主机端口

·探测主机是否在线

·推断主机操作系统类型

### -sT  tcp扫描

全连接扫描 ：  发送一个tcp的连接，不需要root用户即可，容易被探测到

### -sS    SYN扫描

半连接扫描：不是一个完整的tcp连接，只发送一个SYN包，返回		SYN|ACK包说明端口正在监听，如果返回RST包说明端口没有监听程序，痕迹少，不易被发现，不过要root权限

### -sF     FIN扫描

​    秘密扫描   除SYN、ACK其他位置

### 	-sX    Xmas扫描

   秘密扫描    FIN、URG、PUSH位置

### 	-sN   -null扫描

   密码扫描   标志位全为0，发送TCP分组

### 	-sP   ping扫描

​    同时使用ICMP  TCP  ACK 80返回RST说明主机运行

### 	-sU  UDP扫描

   发送0字节UDP包，快速扫描windows的UDP端口

### 	-sA  ACK扫描

  TCP ACK扫描

，防火墙开启时，查看防火墙未过滤端口

### 	-P0

  NMAP扫描前不ping主机

### 	-PT

  扫描前使用TCP  ACK包确定主机是否在运行  默认80端口
	-PS  TCP  SYN扫描

### 	-PI

  ping扫描

### 	-O 

 扫描TCP/IP指纹特征，确定目标主机类型

### 	-v 

 冗余模式扫描，可以得到扫描时的详细信息

### 	-S

   欺骗扫描时，用来指定主机IP
	