# SQL注入

sql注入是web应用程序对用户的输入数据的合法性没有判断，前端传入的数据是攻击者可控的，并且可以带入数据库查询，攻击者可以构造不同的sql语句来实现自己的目的

## 注入之前的尝试

我们可以通过输入带有特殊符号的不同的参数来对输入点进行测试，该位置是否存在注入点。

1

1 and 1=1

1 and 1=2

1 or 1=2

1'

1' and 1=1

1' and 1=2

1' or 1=1

如果出现错误页面就说明存在注入点，特殊符号不仅仅是指"  '  "  也包括()""甚至也可能不止一层

## MySQL与sql注入的一些知识点

在MySQL5.0以上的版本，数据库中存在一个“information_schema”的数据库，我们需要记住该数据库中的三个表，schemamata,tables,columns

·schemamata这个表存放所有数据库的名字，表中数据库的名字字段是schema_name 

·tables表存放所有数据库的库名以及表名，字段分别为table_schema和table_name

·columns表中存放用户创建的所有数据库的库名、表名、字段名，他们的字段名分别是，table_schema,  table_name,  column_name 



## 一些常用的函数

select   查询的字段名  from 库名.表名

limit的用法

limit的格式是limit(n,m)，其中n是开始的位置，m为取几条记录

如select * from test.user limit 1,2

查询所有列从test库中的user表，从第二行开始一共取2行

version()   当前数据库的版本

database()当前网站使用的数据库

user()当前MySQL的用户

三种常用的注释符

1.#

2.--+或者--空格

3./**/    *中的内容会被注释

## union注入

联合注入是在参数输入的地方拼接另一个查询语句，使数据库执行此语句，从而达到目的

union select database() --+

union select table_name from intormation_schema.tables where table_schema=database() --+

