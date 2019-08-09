# ssh远程管理网路设备：

telnet  也可以管理，不过telnet使明文传输  telnet使用23端口

为了提高安全，使用ssh，密码进行了加密  使用22端口

配置ssh：

配置交换机名字

switch(config)#hostname  sw1

配置域名

sw1(config)#ip domain-name ccie.com

配置加密方式

sw1(config)#crypto key generate rsa

配置密码加密长度

512的倍数

设置用户名和密码

sw1(config)#username admin password ccie

或者sw1(config)#username admin  privilege（权限级别）  0  secret ccie

server(config)#line vty 0 4

server(config-line)#exec-timeout 10 0（10分钟没有进行操作，断开连接）

server(config-line)#logging synchronous

server(config-line)#login local

server(config-line)#transport input ssh（选择登陆方式）

ssh -l +用户名 +ip