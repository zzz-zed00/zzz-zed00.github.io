# SQL注入绕过

## 1.空格绕过：

​	/**/    %a0   括号也可以绕过空格 括号两边可以不用加空格如：where（1=1）

## 2.引号绕过：

​	十六进制绕过：将引号括起来的语句用十六进制表示

## 3.逗号绕过：

​	from  for绕过，如select substr(database() from 1 for 1)
​	join绕过union select 1,2   #等价于
​		union select * from (select 1)a join (select 2)b
​	like绕过    limit可以使用offset绕过
​		如select *from news limit 0,1   #等价于
​			select * from news limit 1 offset 0

## 4.大于号>小于号<绕过    

​	greatest()、least()前者返回最大值，后者返回最小值
​	greatest(1,5,6,2,3,1)  返回6
​	between and  #between a and b  返回a和b之间的数据  不包含b

## 5.or   and   xor  not  绕过

​	and 用&&   or用||   xor用|  not用!

## 6.绕过注释符号   过滤注释符号

​	使语句闭合

## 7.=绕过

​	like    rlike  regexp  或者用“或者”

## 8.绕过union  select  where等sql常用语句

​	注释符绕过。。暂定 看不懂
​	大小写绕过  #语句大小写混合输入  id=-1' UnIoN SeLecT
​	内联注释绕过/*！  */
​	双关键字绕过  适用于只过滤一次关键字的注入

## 9.通用绕过

​	编码绕过   urlencode   ascii  hex  unicode

## 10.宽字节注入

​	%df和转义符形成一个特殊字符从而吃掉‘转义符’ 让%df后面的字符逃过转义

## 11.等价函数

​	datadir()=@@datadir等