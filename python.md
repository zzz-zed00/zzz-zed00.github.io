# python学习笔记

<!--more-->

## 输入输出

```             python
print(' '，“ ”)  #输出单双引号皆可  引号括起来就是字符，不括就是整型
print （'''test
	test
	test'''）#换行输出单双引号皆可
	a=input（'  '） #键盘输入a只能是str
	#可以用a=int(a) 将a转化为整型
	 #字符串中\可以标识' 和" ,比如
'i\'m\''ok\''!' 表示 i'm ''ok''!
s=input('as',end='')#如果显示不换行在后面加end=''，默认换行
	#%是取余除法，是永远取整数的除法
```

### 编码

``` python
'ABC'.encode('ascii')
b'ABC'   #将ABC从str转化成bytes
b'ABC'.decode('ascii')
'ABC'  #将bytes转化为str
len()#可以计算字符长度
```

### 参数

``` 
#前面传入参数'{0}，{1}，{2}'.format('a','b','c')
	#%d  double整数型  %.2f  浮点型两位小数
	#%s  str字符串    %
```

### list

``` python
class=['a','b','c']   #class是一个集合，可以增删改的list
len(class)
	3   #list的元素个数
class[0]				#读取第一个元素class[-1]读取倒数第一个元素
class.append('d')  		#添加一个元素在末尾
class.insert(1,'1') 	#添加到索引号为1的位置
class.pop(i)			#删除指定位置元素
class(1)='2'  			#直接赋值给索引号为1的元素，从而替换该元素的值
#list中的元素可以不同，整型、字符串、等等
class1=['l'.'m']      
class2=['n',class1] 	 #list中可以存放class2可以看为二维数组
```

### tuple

``` python
t=（1，2）  		#tuple一经确定不能修改
t=(1,)  			#tuple在定义只有一个元素的时候用逗号消除歧义
t=('a','b',['x','y']) #在创建时可以在tuple中添加一个list从而改变tulp中的元素的目的
```

## 条件判断

### if

``` python
#if语句后面要加:冒号  
	#可以执行多个elif语句
	#if语句执行从上往下，一但符合条件立即结束
import math
def qiujie(a,b,c):
    if (b*b-4*a*c)<0:
        print('无实根')
    else:
        x1=(-b+math.sqrt(b*b-4*a*c))/(2*a)
        x2=(-b-math.sqrt(b*b-4*a*c))/(2*a)
        x=move(x1,x2)
        print(x)
```

## 循环

### while

``` 
	#while语句当条件满足时会一直循环，不满足时退出
	#break可以退出循环，一般与if判断语句一起用
	#continue语句会跳过当前循环，符合本语句的循环会直接跳过
```

## 字典

### dict--dictionary

```  python
d={'a':1,'b':2,'c':3} #a相当于key、页码之类的  可以快速翻页查找目标
	d['a']=4  #可以直接用key来将元素放入，后放入的元素会把前面的冲掉
	d.get('kkk')  #判断key是否在字典中也可以设定
    d.get('kkk',-1)   #返回-1 即当kkk不存在时返回-1
	d.pop('kkk') #删除key之后对应的元素也会被删掉
```

### set

``` python
s=set([1,2,3,])  #set也是一组key值 但是不能存储value，没有重复的key
s=set([1,2,2,3,3,])  #重复元素会被过滤掉
s.add(2)  #add可以添加元素可以重复添加，但会被过滤
```

# 函数

## def

``` python
def a():在随意文件里xx.py中创建一个函数为a
·import xx from a  #将xx中的a函数调用函数可以返回多个值，其实就是一个tuple
```

## 参数

``` python
*num表示把num这个list或者tuple的所有元素变成可变的参数传进去
关键字参数def person(name,age,**k)  #k就是关键字参数 //调用该参数时可以只传入一	个关键字参数
```

## 递归函数

``` python
def digui(n):
    		if n==1:
        			return 1
    		return n * digui(n-1)   # 函数调用自身的一种函数，不过会出现栈溢出的问题

	def digui(n):
    		return digui2(n,1)
	def digui2(n,s):
    		if n==1:
        			return s
    		return digui2(n-1,n*s)   #尾递归可以解决栈溢出问题，但是大多数解释器没优化，故还是会造成栈溢出

```

## 切片操作

``` python
	[0:3]  #切取前3个元素，--不是从1开始，是从第一个元素开始
	[0:5:2] #在前5个元素中，每隔两个取一次
	[:5] #当第一个索引是从0开始时，0可以省略
	[:]  #原样复制一个list
	'asdasdada'  [0:3] #字符串也可以切取，结果也是字符串
	(1,2,3,4,5) [0:2]  #tuple也可以切取，结果为tuple
```

## 迭代

``` python
	for xx in l  #for可以迭代各种对象
	from colletions import Iterable  #collections中的iterable模块可以判断是否可以迭代
	isinstance([1,2,3,4])
```

## 列表生成式

``` python
	list(range(1,10))  #生成1到9的列表
	[x*x for x in range(1,10)]  #生成1*1到9*9的一个列表
	[m+n for m in 'abc' for n in 'xyz']  #双层循环
```

## 生成器

生成器输出用yield ()  yield输出后停止，下次开始时从停止的地方继续

参照杨辉三角

``` python
def yang():
    b=[1]
    while True:    #永真
        yield b     #执行时停止循环，下次执行从下一行开始
        b=[1]+[b[i]+b[i+1]for i in range(len(b)-1)]+[1] #三个列表拼起来
n=0
for t in yang():
    print (t)
    n=n+1
    if n ==10:
        break
```



## 高阶函数

函数值可以赋给变量，函数本身也可以--变量可以指向函数
	**函数可以作为一个参数使用**

``` python
def fun()
		print('a')
	      def gg(x,y)
		print(x,y)
	可以使用gg(x,fun())来调用  不过先返回的函数？
```

## map()/reduce()

``` python
map(fun,3,2,5,6,5,4,2,1)    # map会将后面参数全部带入函数fun中
	reduce(gg,3,2,5,4,5,6,7,)   #函数gg必须为输入两个参数的，map会将3和2参数放		入，并将结果和5一起传入参数，以此类推
```

## 全局变量global

global  告诉解释器定义的为全局变量，声明一个变量变为全局变量

``` python
a=4
def hanshu():
    global a   #定义全局变量
    a=2
    print(a)

def hanshu2():
    a=8
    print(a)

def hanshu3():
    print(a)
hanshu2()
hanshu3()
hanshu()
```



## 转义符

\t可以让输出垂直对齐，\n换行

## 常用函数(·补充)

dir()可以查看对象的使用方法

# 类和对象

``` 
先有类，后有对象
对象调用类中的方法
可以利用   .属性名="属性"   给对象增加属性
初始化方法  __init__
	在初始化方法中设定属性用  self.属性名="属性"
	在对象调用类的时候会自动使用设定的初始化方法
对__init__设置形参可以使初始化方法更加灵活
	class cat():
	def __init__(self,new_name)
		self.name=new_name
	等调用时直接传入形参
	tom=cat("tom")即可将tom赋值给self.name进而传给tom这个对象

__del__会在对象销毁之前调用
__str__能够让print输出对象的时候返回一个字符串而不是地址

同一个类创造出来的对象互不干扰
```

参照

``` python
class stu():        #  创建类
    def stu1(self):     #创建类的方法
        print("%s" %self.name,end="")
    def syu2(self):
        print("%d" %self.id)
dt=stu()

dt.name="dt"
dt.stu1()   #调用类
dt.id=1
dt.syu2()    #调用类
zw=stu()
zw.name="zw"
zw.id=2
zw.stu1()
zw.syu2()
```

## 伪私有属性和方法

```python
定义一个类  class women:
在设定一个属性时在属性名前加两个_可以将属性私有，私有属性只能在方法中调用		，在类外不能调用
	self.__age
同样私有方法也不能在外界访问
	def __sy(self):
     私有属性和私有方法同样可以调用
	xiaofang=women("小芳")
	print(xiaofang._women__age)调用属性
	xiaofang._women__sy()调用方法
```
参考

``` python
class women:
    def __init__(self,name):
        self.name=name
        self.__age=18  #私有属性
    def script(self):
        print("%s是一个%d岁的people"%(self.name,self.__age))  #私有属性在方法内部可以调用
    def __scrt(self):
        print("%s是一个%d岁的people"%(self.name,self.__age))
xiaohua=women("小花")
xiaohua.script()
#print(xiaohua.__age)         #   将本行取消注释可以看到外部不能调用方法内部的私有属性
#xiaohua.__scrt()     #     将本行取消注释可以看到外部不能调用内部私有方法
print(xiaohua._women__age)    #  本行可以看出可以强制调用私有属性
xiaohua._women__scrt()        #   本行可以看出可以强制调用内部的私有方法





#      所以说  以上私有属性和私有方法全是伪的   可以强制调用，不过不建议使用
```

## 继承

``` python
子类会继承父类所有的属性和方法
		class animal:
		class  dog(animal):   #dog可以继承animal的属性和方法
	继承是有传递性的
	子类重写父类继承过来的方法，会调用重写的方法，而不会调用原来的方法
	子类可以扩展父类中的方法，super()函数可以调用父类中的方法
	super().继承的父类的方法，课可以在原父类的方法进行扩展
```

