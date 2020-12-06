# Web了解

## 1.Web的五个概念

```text
1.BS: Browser + Server 
    浏览器服务器架构
        优点:开发成本低,效率快,维护成本低
        缺点:开发的代码都放在服务器上    胖服务器-瘦客户端
            速度和安全性上需要花巨大成本设计

    CS: Client + Server
    客户端服务器架构
        优点: 响应速度快,形式多样,可以实现复杂的业务流程,安全性高
        缺点:需要专门安装特定的软件,局限性较大,开发,维护成本高
```

```text
2.静态页面和动态页面

	静态页面: 服务器不执行的页面
	动态页面: 服务器执行的页面
```

```text
3.客户端和服务端

    客户端:展现信息服务内容
    服务端:提供信息服务内容
```

```
4.端口和端口号(不全,待补充)

	端口就像是酒店的各个房间, 端口号相当于门牌号
```

```
5.前台和后台

    前台:浏览者看到的界面
    后台:管理员看到的界面
```

## 2.Web的服务原理

```text
静态网站原理（浏览器-服务器）

动态网站原理（浏览器-服务器-数据库）

智能网站原理（浏览器-服务器【分析推荐】-数据库）
```

## 3.互联网的通讯原理

```text
	一台电脑访问另外一台电脑的资源,寻址过程(IP地址, 域名, 端口号, DNS), IP地址是用来区分每台计算机的标识,因为IP地址记忆不方便,给IP地址绑定一个名字,叫做域名. 
	客户端输入域名,在最近的机房做DNS解析, DNS将域名转化为IP地址进行访问
```



# PHP基础

## 1.PHP的简介

```
PHP:超文本预处理器,是一种在服务器端运行的开源脚本语言

	优点:开源,免费,跨平台,入门简单,
```

## 2.PHP的使用环境

```
LNMP: Linux + Nignx + Mysql + PHP

WAMP: Windows + Apache + Mysql + PHP
```

## 3.常用的命令

```text
DOS命令:
	切换盘符	盘符+英文冒号
	进入目录:	cd 目录地址

Apache命令
	httpd -v	查看apache版本号
	httpd -t	检测运行环境
	
查看端口号占用命令
	查看	netstat -ano
	查找	netstat -ano |findstr 80
```



## 3.PHP的工作过程

```
	当用户在浏览器地址输入要访问的PHP页面文件名, 会触发一个请求,并把请求发到web服务器,服务器接受这个请求,并根据后缀判断是不是一个PHP请求,服务器调出用户要访问的PHP,发给PHP引擎,PHP引擎将会对服务器传递的文件进行处理,并动态的生成相应的HTML页面,
	PHP引擎将生成HTML页面返回给WEB服务器。WEB服务器再将HTML页面返回给客户端浏览器。
```

## 4.PHP的文件格式

```text
1、标准格式
		<?php ?>
		【注】纯PHP文件 不要结尾

2.<?php (常用模式)

3. 短标记格式(了解)	
		<? ?>
		需要修改php.ini的short_open_tag = On
		
4.每一条语句以英文半角的分号结尾
```

## 5.PHP的注释

```PHP
#		单行
//		单行
/**/	多行
```

## 6.PHP的输出

```php
echo:		可以输入多个变量,中间用逗号隔开
print:		只能输出一个
print_r:	输出复杂的数据类型
var_dump:	可以输出详细信息, 数据类型和数据长度
```

## 7.PHP的变量命名规范

```text
1.以$符开头
2.字母数字下划线组成, 不能以数字开头
3.变量名区分大小写, 一般使用小写, 使用驼峰命名法
4.变量名命名 要见名知意
5.变量赋值	变量名 = 变量值;	例: $a = 10;
例:
	驼峰命名:
		$userName	小驼峰
		$UserName 	大驼峰
	下划线命名:
		$user_name
```

## 8.PHP的可变变量

```php
//变量名可以变,将变量名储存在另一个变量中
<?php
    $a = 10;
	$b = 'a';
	echo $$b;	//输出10
```

## 9.PHP的变量传递

```text
1、参数的传递有两种，值传递和地址传递
2、&表示获取变量的地址
3、值传递中，一个变量变了，另一个变量没有影响，因为是两个空间
4、地址传递中，一个变量变了，另一个也变了，因为两个变量指向同一个空间
```

```php
//值传递 例:
<?php
	$num1 = 10;		//将10赋值给$num1
	$num2 = $num1;	//将$num1的值赋给$num2
	$num2 = 20;		//将10赋值给$num20
	echo $num1		//10
```

```php
//引用传递 例:
<?php
    $num1 = 10;		//将10赋给$num1
	$num2 = &$num1;	//将num1的地址赋给$num2
	$num2 = 20;		//将20赋值给$num2
	echo $num1;		//20
```

## 10.PHP的变量使用

### 1.变量的销毁

```php
<?php
    $a = 1;
 	unset($a);
	echo $a;

//unset销毁的是变量名, 变量值由PHP垃圾回收机制销毁
```

### 2.变量是否被定义

```php
<?php
	$a = 1;
	var_dump(isset($a));

//返回true和false
```

### 3.变量是否为空

```php
<?php
	$a = 10;
	var_dump(empty($a));

//返回true(为空)和false(不为空)
```

## 11.PHP的常量定义

```
常量的定义:
	1.常量命名没有$符号
	2.常量名推荐使用大写
	3.常量可以不用理会变量的作用域在任何地方定义和访问
	4.常量一旦定义就不能重新定义或者取消定义
	5.常量的值只能是标量
```

### 1.使用函数define()定义常量

```text
格式: define(常量名, 值, [可选参数:是否区别大小写]);(可选参数true/false;  默认为false)
```

```php
<?php
    define('NAME', 'admin'); //区分大小写
	define('NAME', 'admin', true);	//不区分大小写

//PHP版本7.0和7.1, 7.2可以正常使用不区分大小写, 7.3之后不赞成使用区分大小写
```

### 2.使用特殊字符定义常量

```php
<?php
    define('%%', 'admin');
	echo constant('%%');
//定义常量可以使用特殊字符, 但是在调用的时候必须用constant关键字
```

###  3.使用关键字const定义常量

```php
<?php
	const NAME = 'admin';
	echo NAME;	//admin
```

### 4.判断常量是否已经定义

```php
//使用defined()函数来判断常量是否已经定义

if(!defined('NAME')){	
	define('NAME','berry');
}
echo NAME;	//berry
```

### 5.define和const的区别

```text
1.使用const使得代码简单易读, const是一个语言解构,define是一个函数
2.const的编译速度比define快
3.const用于类成员变量的定义,一经定义,不可修改.define不可用于类成员变量定义,可用于全局常量
4.const可以在类中使用,define不能
5.const不能在条件语句中定义常量
```

### 6.PHP的预定义常量

```php
PHP_VERSION			//PHP版本号
PHP_OS				//PHP操作系统
PHP_INT_MAX			//PHP中整型最大值
```

### 7.PHP的魔术常量

```php
__LINE__		//返回获取当前行号
__FILE__		//返回所在文件的完整路径.包含文件名
__DIR__			//返回文件所在的目录
__FUNCTION__	//返回所在的函数名称(返回function形式)
__CLASS__		//返回所在类的名称
__METHOD__		//返回所在类方法的名称(返回class::function形式)
__NAMESPACE__	//返回当前命名空间的名称(区分大小写)
__TRAIT__		//返回trait被定义时的名字(区分大小写),包括其被声明的作用区域
```

```php
一些相关东西 要背
    ::1							ipv6 表示方式 其实就是 127.0.0.1
    $_SERVER					超全局数组
    $_SERVER['HTTP_HOST']		获取主机名
    $_SERVER['REMOTE_ADDR']		获取客户端IP地址
    $_SERVER['HTTP_REFERER']	获取来源页的地址	
```



## 12.PHP的数据类型

```text
标量:
	整型	int		浮点型	float
	字符串	string	布尔型	true false

混合类型:
	数组  array	对象	object

特殊类型
	资源	resource	空 null
```

### 1.整型

```php
//integer(int): 存整数	PHP支持8, 10, 16进制的整数
<?php
$num1=10;		//十进制
$num2=010;		//八进制（数字前面加0）
$num3=0x10;		//十六进制（数字前面加0x）

echo $num1,'<br>';		//10
echo $num2,'<br>';		//8
echo $num3;				//16
```

#### 进制转换

| 机制     | 缩写 | 单词          |
| -------- | ---- | ------------- |
| 十进制   | dec  | decimalist    |
| 二进制   | bin  | binary        |
| 八进制   | oct  | octonary      |
| 十六进制 | hex  | hexdecimalist |

PHP提供的转换函数

```php
echo decbin(123),'<br>';   //十进制转二进制
echo bindec(1111011),'<br>';	//二进制转十进制
echo dechex(123),'<br>';		//十进制转十六进制
echo hexdec('7b'),'<br>';		//十六进制转十进制
echo decoct(123);				//十进制转八进制
```

### 2.浮点型

```
float:	小数		浮点数在内存中保存的近似值	普通声明	$a = 1.2;
注意: 如果一个整数超出了整型的范围,会自动转为浮点型
```

```php
//浮点数不能参与比较
	var_dump(0.9==(1-0.1));		//bool(true) 
    echo '<br>';
    var_dump(0.1==(1-0.9));		//bool(false) 
```

```php
//如果浮点数要比较，必须确定比较的位数
var_dump(bccomp(0.1,1-0.9,5));	//比较小数点后面5位  int(0)  0表示相等
```

### 3.布尔型

```php
<?php
$flag=false;
var_dump($flag);	//bool(false) 

$flag=true;
var_dump($flag);	//bool(true) 
```

### 4.字符串类型

```php
//单引号字符串是真正的字符串
<?php
    $name='tom';
    echo '我的名字叫$name','<br>';	//我的名字叫$name
    echo "我的名字叫$name",'<br>';	//我的名字叫tom
```

```text
1.单引号不解析变量, 双引号能解析变量

2.单引号不解析特殊字符,双引号解析特殊字符	,但单引号能解析转义字符 \ \

3.单引号不能嵌套单引号, 双引号不能嵌套双引号, 单双引号可以互相嵌套

4.单引号的执行效率比双引号高, 能用单引号就用单引号

5.双引号中嵌套单引号再嵌套变量, 变量会被解析

6.变量名如果在前要加{}, 变量会被解析
```
#### 字符串定界符

```
1、有<<<开头，后面跟的是标识符
2、字符串定界符的结束符必须顶格写，前面不能有任何的空白字符
3、字符串定界符分为两种，heredoc（双引号），nowdoc（单引号）
```

```php
<?php	//heredoc(双引号)
	$name = 'aitmy';
	echo <<<name 名字随意起吧
name;

<?php	//nowdoc(单引号)
	$name = 'aitmy';
	echo <<<'name' 名字随意起吧
name;
```

### 5.数组类型

```php
数组的声明
    索引数组:
		$arr = array(1,2,34,56);	PHP7后 $arr = [1,2,34,5,6];
	关联数组:
		$arr = array('name'=>'aitmy'); $arr = ['name'=>'aitmy'];
		键: 不可重复, 值可重复
```

```php
注意1: 在PHP7.1中开始支持数组的赋值
    $num1 = 10;
    $num2 = 20;
    [$num1, $num2] = [$num2, $num1];
    echo $num1,'<br>, $num2';

注意2: 在PHP7.1开始,字符串可以通过数组的方式去调用
	echo 'abc'[0],'<br>';	//a 从左边开始数覅一个
	echo 'abc'[-1],'<br>;	//c 从右边开始取第一个
	
1.数组在内存中一段连续的空间
2.如果要保存同一类型的多个数据就使用数组
```

### 6.对象object

### 7.资源resource

### 8.null

```html
为null的几种情况
        1、变量未定义
        2、变量声明未赋值
        3、直接赋值为null
```

### 9.类型的判断

```php
<?php
	gettype()		//获取变量的数据类型
	is_array()		//判断是否是数组
	is_bool()		//判断是不是布尔型
	is_float()		//判断是不是浮点型
	is_int()		//判断是不是整型
	is_string()		//判断是不是字符串
	is_object()		//判断是不是对象
	is_numeric()	//判断是不是数字
	is_resource()	//判断是不是资源
	is_scalar()		//判断是不是标量
    is_null()		//判断是不是空
```



## 13.PHP的类型转换

### 1.自动类型转换

```php
//自动类型转换：当提供的类型和需要的类型不一致的时候会自动进行类型转换
<?php	
    $num=10;
    if($num){   //自动将数字转成布尔型
        echo 'aa';
    }else{
        echo 'bb';
    }
    ---------------------------------
    echo '20'-10;	//自动的将字符串转成数字
```

#### 1.1PHP为fasle的几种情况

```php
<?php	//为假
	var_dump((bool)0);			//bool(false) 整型的0
	var_dump((bool)0.0);		//bool(false) 浮点型的0.0
	var_dump((bool)'0');		//bool(false) 字符串的0
	var_dump((bool)'');			//bool(false) 空字符串
	var_dump((bool)array());	//bool(false) 空数组
	var_dump((bool)null);		//bool(false) 空资源
	var_dump(boolval(false));	//bool(false) 布尔值的假
			1、整型的0 为假，其他的都为真
			2、浮点型0.0 为假，小数点后 只要有一个非0数字就为真
			3、空字符串为假 只要里面有个空格都为真
			4、空字符的0为假 其他的都是真的
			5、null 空 为假
			6、未声明成功的资源也为假
	//为真
    var_dump((bool)1);			//bool(true) 整型的1 
    var_dump((bool)-10);		//bool(true) 整型的值
    var_dump((bool)'0.0');		//bool(true) 字符串的0.0
    var_dump((bool)'00');		//bool(true) 字符串的00
    var_dump((bool)'false');	//bool(true) 字符串的false
    var_dump((bool)'null');		//bool(true) 字符串的null
    var_dump((bool)'abc');		//bool(true) 字符串的非0值
    var_dump((bool)array(1));	//bool(true) 数组的值
    var_dump((bool)array(false));//bool(true) 数组的false
```



### 2.强制类型转换

```php
//语法：（数据类型）数据
//强制类型转换函数:strval(); intval(); floatval();	boolval();
//类型转换函数 并不会改变变量本身 而是生成新的变量 转换的是值
<?php
   $num1='12';
    var_dump($num1,(int)$num1,(float)$num1);   //string(2) "12" int(12) float(12)

settype(变量, 类型)函数
		settype($a, 'int');
		【注】settype 改变的是变量本身 而且第二个参数必须是字符类型的
		settype($a, 'null');
		$a = null; 就是相当于把$a赋值为null
```



## 14.PHP的运算符

### 1.算数运算符

| 一元运算符 | 二元运算符 |
| ---------- | ---------- |
| ++         | +          |
| --         | -          |
|            | *          |
|            | /          |
|            | %   (取模) |

```php
//注意：在PHP中，算术运算符只能做数学运算。
<?php
   echo '10'+'20','<br>';		//30
   echo '10ab'+'20cd','<br>';	//30
   echo 'ab10'+'cd20','<br>';	//0
```

```
++前置	先自增再运算
++后置	先运算再自增
--前置	先自增再运算
--后置	先运算再自增
```

### 2.关系运算符

```php
>
>=
<
<=
==
!=
===
!==
//运算结果为布尔值的真和假
```

### 3.逻辑运算符

```php
&	与：运算符两边的表达式都要计算
|	或：运算符两边的表达式都要计算
    
&&	逻辑与：如果有一个条件为假都为假
||	逻辑或: 如果有一个条件为真即为真
!	非 取反
```

### 4.赋值运算符

```php
=	//复制
+=	//a+=b		a=a+b
-=
*=
/=
%=
```

### 5.三元运算符

```php
表达式 ? 值1 : 值2 =;
表达式的值为真,返回值1, 为假返回值2

<?php
    $num = 10;
	echo $num>11 ? '假' : '真';
```

### 6.合并运算符

```php
//PHP7.0 开始支持
<?php
	echo $name??'姓名不祥';	//姓名不祥
```



## 15.PHP的字符串链接

```php
<?php
	echo 'aa'.'bb';		//字符串链接	aabb
```

## 16.PHP的错误抑制符

```php
<?php
	echo @($aa+$bb);	//错误抑制
```

17.PHP的判断 

## 17.PHP的判断

### 1.PHP的if判断

```php
//单分支
<?php
    if (条件) {
       //代码块
    }
```

```php
// 双分支
<?php
    if(条件){
        //代码块1
    }else{
        //代码块2
    }
```

```php
//多分支
<?php
	if(条件){

    } elseif(条件) {    //注意：elseif之间没有空格

    } else {

    }
```

### 2.switch case判断

```php
<?php
	switch(表达式){
        case 常量：
            //代码块
            break;
        case 常量：
            //代码块
            break;
   		default:
        	//代码块
	}
```

## 18.PHP的循环

### 1.for循环

```php
//for循环格式
for(初始值;条件;增量){
	//循环体
}
```

```php
//for 例:
<?php
    for($i=1;$i<=10;$i+=2){
        echo "{$i}:锄禾日当午<br>";
    }
输出结果:
    1:锄禾日当午
    3:锄禾日当午
    5:锄禾日当午
    7:锄禾日当午
    9:锄禾日当午
```

```php
例2:		//for死循环

<?php
for($i=1;$i<=10;){
	
}
//死循环，$i永远等于1，1永远小于10，条件永远为true

<?php
for($i=1;;$i++){
}
//死循环，只要没有条件都是死循环

<?php
for(;;){
}
//这是一个经典的死循环
```

### 2.while  do-while

```php
while(条件){
    
}
执行流程：判断表达式是否成立 如果成立就执行循环体 然后继续判断表达式是否成立 如果成立在执行循环体 知道不成立 跳出循环
-------------------------
do{
    
}while(条件)
执行流程：首先先执行一次循环体 然后判断表达式是否成立 如果成立再执行循环体 如此往复 直到条件不成立就结束循环
```

### 3.三种循环的区别

```text
1、for、while、do-while可以相互替换

2、如果明确知道循环多少次首先for循环，如要要循环到条件不成立为止选while或do-while

3、先判断再执行选while，先执行再判断选do-while

4、while循环条件不成立就不执行，do-while至少执行一次
```

### 4.多语句表达

```php
//初始值、增量可以由多条语句组成
<?php
for($i=1,$j=9;$i<=$j;$i++,$j--){
	echo "10可以分成{$i}和{$j}<br>";
}
//运行结果
/*
10可以分成1和9
10可以分成2和8
10可以分成3和7
10可以分成4和6
10可以分成5和5
*/

小结：初始值、增量可以写多个表达式，但是条件一般只写一个，如果条件写多个，只是最后一个条件起作用
```

### 5.双重循环

1.打印阶梯数

```php
<?php
for($i=1;$i<=9;$i++){	//循环行
	for($j=1;$j<=$i;$j++){	//循环列
		echo $j,'&nbsp;';
	}
	echo '<br>';
}
//运行结果
1 
1 2 
1 2 3 
1 2 3 4 
1 2 3 4 5 
1 2 3 4 5 6 
1 2 3 4 5 6 7 
1 2 3 4 5 6 7 8 
1 2 3 4 5 6 7 8 9
```

2.打印99乘法表

```php
<style type="text/css">
	table{
		width:980px;
	}
	table,td{
		border:solid 1px #0000FF;
		border-collapse:collapse;
	}
	td{
		height:40px;	
	}
</style>

<table>
<?php
for($i=1;$i<=9;$i++){	//行
	echo '<tr>';
	for($j=1;$j<=$i;$j++){	//列
		echo "<td>{$j}*{$i}=".($j*$i).'</td>';
	}
	echo '</tr>';
}
?>
</table>
```

### 6.foreach循环

```php
//语法一
foreach(数组 as 值){
}
//语法二
foreach(数组 as 键=>值){
}
```

```php
<?php
$stu=['tom','berry','ketty'];
foreach($stu as $v){
	echo $v,'<br>';
}
/**
tom
berry
ketty
*/
echo '<hr>';
-----------------------------------------------------------
foreach($stu as $k=>$v){
	echo "{$k}:{$v}<br>";
}
/**
0:tom
1:berry
2:ketty
*/
```

### 7.continue和break的区别

```text
1.continue是跳过本次循环进入下一次循环
2.break 是结束循环 
```

8.中断多重循环

```php
//break和continue默认中断、跳出1重循环，如果调中断、跳出多重循环，在后面加一个数字。
<?php
for($i=1; $i<=10; $i++) {
	for($j=1;$j<=$i;$j++){
		echo $j.'&nbsp;';
		if($j==5){
			break 2;   //中断2重循环
		}
	}	
	echo '<br>';
}
//运行结果
1 
1 2 
1 2 3 
1 2 3 4 
1 2 3 4 5 
```

## 19.PHP的语法替换

```php
1.php中除了do-while以外，其他的语法结构都有替代语法
2.规则：左大括号变冒号,右大括号变endXXX
3.在混编的时候用替代语法
```

```php
//if的替代语法
    if():

    elseif():

    else:

    endif;
//switch替代语法
    switch():

    endswitch;
//for
    for():

    endfor;
//while
    while():

    endwhile;
//foreach
    foreach():

    endforeach;
```

## 20.PHP的函数

### 1.声明函数

```php
//通过函数名()调用函数
function 函数名(参数1，参数2，...){
    //函数体
}
```

```php
<?php
//定义函数
function show() {
	echo '锄禾日当午<br>';
}
//调用
show();		//锄禾日当午
SHOW();		//锄禾日当午  函数名不区分大小写
```

### 2.可变函数

```php
//将函数名存储到变量中
<?php
function show($args) {
	echo $args,'<br>';
}
$str='show';	//将函数名保存到变量中
$str('锄禾日当午');
```

```php
例题:
<?php
 //中文显示
function showChinese() {
	echo '锄禾日当午<br>';
}
//英文显示
function showEnglish() {
	echo 'chu he re dang wu<br>';
}
//测试
$fun=rand(1,10)%2?'showChinese':'showEnglish';   //可变变量
$fun();
```

### 3.匿名函数

```php
//匿名函数就是没有名字的函数
<?php
//匿名函数
$fun=function(){
	echo '锄禾日当午<br>';
};
//匿名函数调用
$fun();
```

### 4.函数的传参

```
1.函数的参数有形式参数和实际参数
2.形式参数是定义函数时候的参数，只起形式的作用，没有具体的值
3.实际参数的调用函数时候的参数，有具体的值
```

```php
<?php
function fun($num1,$num2) {
	echo $num1+$num2;
}
fun(10,20);		//30
```

```php
//默认情况下，参数的传递是值传递
<?php
    $num=10;
    function fun($args) {
        $args=100;
    }
    fun($num);
    echo $num;		//10
```

```php
//地址传递
<?php
    $num=10;
    //地址传递
    function fun(&$args) {   //&符表示取地址
        $args=100;
    }
    fun($num);
    echo $num;		//100
```

```
1、函数的参数默认是值传递

2、如果要传递地址，在参数前面加&

3、如果是地址传递，不能直接写值
```

### 5.函数传参的默认值

```php
//在定义函数的时候给形参赋值就是参数的默认值
<?php
//参数的默认值
function fun($name,$add='地址不详') {
	echo '姓名：'.$name,'<br>';
	echo '地址：'.$add,'<hr>';
}
//测试
fun('tom','北京');
fun('berry');
```

```php
//默认值可以使用常量,不能用变量
------------------------------------------------
<?php	//使用常量
define('ADD','地址不详');
function fun($name,$add=ADD) {    //默认值可以使用常量
	echo '姓名：'.$name,'<br>';
	echo '地址：'.$add,'<hr>';
}
//测试
fun('berry');
-------------------------------------------------
<?php	//使用变量
$str='地址不详'
function fun($name,$add=$str) {   //错误，默认值可以使用变量
	echo '姓名：'.$name,'<br>';
	echo '地址：'.$add,'<hr>';
}
```

```
小结:
1、形参也可以不给 但是一般都会给 形参可以给多个 数量 一般不会超过五个
2、形参可以给默认值,给了默认值之后,调用的时候给实参就是实参的值,不给就是默认值
3、形参给默认值的时候 一般放在最后
4、函数调用 不分先后顺序
5、函数不能重复定义
```

### 6.参数约束

#### 1.定义变长参数

```php
<?php
// ...$hobby包含了除了前面两个参数以外的所有参数
function fun($name,$age,...$hobby) {
	echo '姓名：'.$name,'<br>';
	echo '年龄：'.$age,'<br>';
	print_r($hobby);
	echo '<hr>';
}
fun('tom',22);
fun('berry',25,'读书','睡觉');
//运行结果
	姓名: tom
    年龄: 22
    Array()
-------------------
     姓名: berry
     年龄: 25
     Array([0]=>读书 [1]=>睡觉)
```

```php
例题:
	function fun(...$args) {
	print_r($args);
        echo '<br>';
    }
    $num=[10,20];
    fun(...$num);   //将数组中的参数展开
    //运行结果
    /*
    Array
    (
        [0] => 10
        [1] => 20
    )
    */
```

#### 2.参数类型约束

```php
//类型约束
function fun(string $name,int $age) {
	echo "姓名：{$name},'<br>'";
	echo "年龄：{$age}<br>";
}
fun('tom',22);
//约束$name是字符串型，$age是整型
```

#### 3.返回值约束

```php
//可以约束 string  int  float  bool  数组
function fun(int $num1,int $num2):int {  //必须返回整型
	return $num1+$num2;
}
echo fun(10,20);		//30
```

```php
//约束返回值类型是数组
function fun():array {
    
}
fun();

//约束return后不能有返回值  7.1版本后中开始支持
function fun():void {		void:空的意思
    return;
}
fun();
```

#### 7.函数的return

```php
<?php
	echo '1111';	//输出1111
	return;			//return后的任何代码不再执行
	echo '2222';

//return只能中断当前页面,如果包含的有文件,只能中断包含文件;
```

```php
//如果想要终止脚本的执行, 可以使用exit(); 或 die();
echo 'aaa';
exit();  //die()
echo 'bbb';
```

##### 7.1返回结果

```php
//test.php
<?php
return array('name'=>'tom','sex'=>'男');
```

```php
//demo.php
<?php
$stu=require './test.php';
print_r($stu);  //Array ( [name] => tom [sex] => 男 ) 

//在项目中引入配置文件就使用这种方法
```

##### 7.2 函数的返回和终止

```php
return在函数中使用作用有:
	1、终止函数执行
	2.返回值
---------------------------------------------
	function fun() {
        echo 'aaa';
        return ;		//终止函数执行
        echo 'bbb';
    }
    fun();   //aaa
---------------------------------------------
    function fun() {
        return 10;	//返回值
    }
    echo fun();		//10
```

## 21.变量的作用域

1.外部变量: 在函数外部定义的变量

2.内部变量: 在函数内部定义的变量

3.超全局变量: 在函数内部和外部都可以访问的变量

```php
	$_SERVER	服务器和执行环境的信息
	$GLOBALS	引用全局作用域中可用的变量
	$_GET		接受以get方式传过来的参数
	$_POST		接受post方式传过来的参数
	$_FILES		获取文件上传信息
	$_REQUEST	Request 变量
	$_ENV		环境变量
	$_COOKIE
    $_SESSION	
```

```php
//函数内部变量默认不能访问函数外部变量
<?php
    $num = 10;
	function fun() 
    {
        echo $num;
    }
	
	fun();
//结果:	Notice: Undefined variable: num 
```

```php
//获取超全局变量的值
<?php
    $_POST['num'] = 10;	//将10赋值给$_POST超全局变量
function fun()
{
    echo $_POST['num'];	//获取$_POST超全局变量的值
}
fun();

//结果:	10

--------------------------------------------------------------

<?php
    function fun()
	{
    	$_GET['num'] = 10;		//将10赋值给$_GET超全局变量
	}

fun();
echo $_GET['get'];	 //打印超全局变量的值

//结果:	10
```

### 21.1在函数内部访问全局变量

```php
<?php
    $num = 10;					//定义一个外部变量
	function fun()
    {
        echo $GLOBALS['num'];	//将输出全局的$num;
    }

	fun();
//结果:	10;

<?php
    function fun() {
        $GLOBALS['num']=10;  //将值付给全局的$num
    }
    fun();
    echo $num;   //10
```

### 21.2  global关键字

```php
<?php
    $num = 10;
	function fun()
    {
        global $num; //将全局变量的$num的地址引入到函数内部
            		 //相当于$num = &GLOBALS['num'];	
        echo $num;	 //10
        $num = 100;
    }
	fun();
	echo '<br>';
	echo $num;		 //100
-----------------------------------------------------------
＜?php
    $num = 10;
	function fun()
    {
        global $num;
        unset($num);	//销毁的是引用,不是具体的值
    }
	fun();
	echo $num;			//10
```

小结:

​		１.$GLOBALS保存的是全局变量的所有的值

```php
<?php
    $a=10;
    $b=20;
    function show() {
        echo '<pre>';
        var_dump($GLOBALS);   //是一个数组，保存的是全局变量的所有的值
    }
    show();
```

​		 2.global用于创建一个全局变量的引用

```php
<?php
    /*
    define('PI',3.14);
    function fun() {
        echo PI;   //3.14
    }
    fun();
    echo '<br>';
    */
    -------------------------------------
    function fun() {
        define('PI',3.14);
    }
    fun();
    echo PI;   //3.14
```

### 21.3 静态变量

静态变量一般指的是 静态局部变量;	静态变量只初始化一次

```php
<?php
	function fun()
	{
    	$num = 10;	//普通变量每调用一次初始化一次,调用完毕销毁
    	$num++;
    	echo $num, '<br>';
	}
	fun();	//11
	fun();	//11

----------------------------------------------------------
    
<?php
    function fun(()
    {
        static $num = 10;//静态变量只初始化一次,调用完毕不销毁,第二次调用时就不再初始化
        $num++;
        echo $num,'＜br>';
    }
    fun();	//11
    fun();	//12
```

### 21.4 常量和静态变量的区别

1. 常量和静态变量都是初始化一次
2. 常量不能改变值,  静态变量可以改变值
3. 常量没有作用域, 静态变量有作用域

```php
<?php
    function fun1()
    {
		define('num', 10);
    }
	function fun2()
    {
        echo num;	//10
    }
	fun1();
	fun2();
-------------------------------------------------------------
<?php
    function fun1()
    {
		static $num = 10;
    }
	function fun2()
    {
        echo $num;  //Notice: Undefined variable: num 因为静态变量是有作用域的
    }
	fun1();
	fun2();
```

### 21.5 匿名函数 use()

默认情况下,函数内部不能访问函数外部的变量, 但是在匿名函数中, 可以通过use将外部变量引入匿名函数中

```php
<?php
    $num = 10;
	$fun = function() use($num)	//将$num引入到匿名函数中
    {
        echo $num;
    };
	$fun();		//10
```

思考：如何在函数内部访问函数外部变量

​	1.使用超全局变量

​	2.$GLOBALS

​	3.global

​	4.use 将函数外部变量引入到匿名函数内部

```php
<?php
    $num=10;
    function test() {
        $num=20;
        $fun=function() use($num) {   //只能引入一层
            echo $num;
        };
        $fun();
    }
    test();    //20
```

use可以引入值, 也可以引入地址

```php
<?php
    $num=10;
    $fun=function()use(&$num){   //use可以传地址
        $num=100;
    };
    $fun();
    echo $num;  //100
```

## 22. PHP的递归

递归需要的几个条件

​	1.要有边界条件, 也就是递归出口(退出递归)

​	2.递归前进段和递归返回段, 也就是最后的值

​	3.当边界条件(递归出口) 不满足时, 递归前进; 当边界条件() 

```text
函数内部自己调用自己; 两个元素, 一个是递归点, 一个是递归出口
```

```php
<?php			//输出9,8,7,6,5,4...
    function fun($num)
	{
		echo $num;
    	if ($num == 1) {	//递归出口
            return;
            fun($num-1); //递归点
        }
	}
	fun(9);
```

```php
<?php			//从1加到100
    function fun($num)
    {
		if ($num == 1) {
            return 1;
            return $num+fun($num-1);
        }
    }
	echo fun(100);

//分析
/*
第n次执行			结果
fun (100)		  100+fun(99)
=				  100+99+fun(98)
=				  100+99+98+fun(97)
=				  100+99+98+...+fun(1)
=				  100+99+98+...........+1
*/
```

```php
<?php
    function fun()
    {
		if ($n==1 || $n==2) {
            return 1;
            return fun($n-1)+fun($n-2);	//第n个斐波那契数等于前两个数之和
        }
    }
	echo fun(5)
/*
fun(5) = fun(4)+fun(3)
		= fun(3)+fun(2)
		=(fbnq(2)+fbnq(1))*2+fbnq(2)
		=(1+1)*2+1
		=5
*/
//打印前10个斐波那契数
for($i=1;$i<=10;$i++)
	echo fbnq($i),'&nbsp;';   //1 1 2 3 5 8 13 21 34 55 
```

## 23.PHP的包含文件





## PHP的数据提交

1. get 	2.put

```html
<form method="post" action=""></form>
<form method="get" action=""></form>
```

2.get和post的区别

```text
1.get提交在地址栏上可以看到参数, post提交在地址栏看不到参数
2.get安全性低, post安全性高
3.get提交是参数一个一个的提交, post提交是所有参数作为一个整体一起提交
4.get提交一般不超过255个字节, post提交的大小取决于服务器
5.get灵活,只要页面的跳转就可以传递参数; post提交需要有表单的参与
```

```php
4-
	// 在php.ini中，可以配置post提交的大小
	post_max_size = 8M
```

```php+HTML
5-
    1、 html跳转
       <a href="index.php?name=tom&age=20">跳转</a>

    2、JS跳转
    <script type="text/javascript">
        location.href='index.php?name=tom&age=20';
        location.assign('index.php?name=tom&age=20');
        location.replace('index.php?name=tom&age=20');
    </script>

    3、PHP跳转
    header('location:index.php?name=tom&age=22')
```

## PHP服务器接受数据的三种方式

```text
$_GET:	数组类型, 保存的GET提交的值
$_POST: 数组类型, 保存POST提交的值
$_REQUEST: 数组类型, 保存GET和POST提交的值
```

HTML页面

```html
<body>
<!--表单提交数据-->
<form method="get" action="./2-demo2.php">
	语文： <input type="text" name="ch"> <br />
	数学： <input type="text" name="math"> <br />
	<input type="submit" name="button" value="提交"> <br><br>
</form>
<!--超链接提交数据-->
<a href="2-demo2.php?ch=77&math=88">跳转</a> <br><br>
<!--js提交数据-->
<input type="button" value="点击" onclick="location.href='2-demo2.php?ch=66&math=55'"> <br><br>

<input type="button" value="点击" onclick="location.assign('2-demo2.php?ch=11&math=22')">
</body>
```

PHP页面

```PHP
<?php
//post数组中不为空
if(!empty($_POST)) {
	echo '这是post提交的数据<br>';
	echo '语文：'.$_POST['ch'],'<br>';
	echo '数学：'.$_POST['math'],'<br>';
}
echo '<hr>';
//获取get提交的数据
if(!empty($_GET)){
	echo '这是get提交的数据<br>';
	echo '语文：'.$_GET['ch'],'<br>';
	echo '数学：'.$_GET['math'],'<br>';
}
echo '<hr>';
//既能获取get又能获取post提交的数据
echo $_REQUEST['ch'],'<br>';
echo $_REQUEST['math'];
```

在一个请求中，既有get又有post，get和post传递的名字是一样的，这时候通过$_REQUET获取的数据是什么?

```PHP
//结果取决于配置文件
request_order = "GP"  # 先获取GET，在获取POST值
```

```php+HTML
<?php
if(!empty($_POST)){
	echo '姓名：'.$_REQUEST['username'],'<br>';
}
?>
<form method="post" action="?username=berry">
	姓名： <input type="text" name="username"><br />
	<input type="submit" name="button" value="提交">
</form>
分析：先获取GET的username,再获取post的username，后面的将前面的值覆盖
```

小结：

1、在开发的时候，如果明确是post提交就使用`$_POST`获取，如果明确get提交就用`$_GET`获取

2、request获取效率低，尽可能不要使用，除非提交的类型不确定的情况下才使用。

## PHP的参数传递

```php+HTML
//复选框的命名要加[]
<body>
<?php
if(isset($_POST['button'])) {
	print_r($_POST['hobby']);
}
?>
<form method="post" action="">
	爱好： 
	<input type="checkbox" name="hobby[]" value='爬山'>爬山
	<input type="checkbox" name="hobby[]" value='抽烟'>抽烟
	<input type="checkbox" name="hobby[]" value='喝酒'>喝酒
	<input type="checkbox" name="hobby[]" value='烫头'>烫头
	<input type="submit" name="button" value="提交">
</form>
</body>
```

```php+html
<body>
<?php
if(isset($_POST['button'])) {
	echo '姓名：'.$_POST['username'].'<br>';
	echo '密码：'.$_POST['pwd'].'<br>';
	echo '性别：'.$_POST['sex'].'<br>';
	echo '爱好：',isset($_POST['hobby'])?implode(',',$_POST['hobby']):'没有爱好','<br>';
	echo '籍贯：'.$_POST['jiguan'],'<br>';
	echo '留言：'.$_POST['words'];
}
?>
<form method="post" action="">
	姓名： <input type="text" name="username"> <br />
	密码： <input type="password" name="pwd"> <br />
	性别： <input type="radio" name="sex" value='1' checked>男
		   <input type="radio" name="sex" value='0'>女 <br />
	爱好： 
	<input type="checkbox" name="hobby[]" value='爬山'>爬山
	<input type="checkbox" name="hobby[]" value='抽烟'>抽烟
	<input type="checkbox" name="hobby[]" value='喝酒'>喝酒
	<input type="checkbox" name="hobby[]" value='烫头'>烫头 <br />
	籍贯：
	<select name="jiguan">
		<option value="021">上海</option>
		<option value="010">北京</option>
	</select> <br>
	留言： <textarea name="words" rows="5" cols="30"></textarea> <br />

	<input type="submit" name="button" value="提交">
</form>
</body>
```

小结：

1、表单提交到本页面需要判断一下是否有post提交

2、数组的提交表单元素的名字必须带有[]。

## PHP文件上传

1. 文件域

```php
<input type="file" name="image">
```

表单的enctype属性

​	默认情况下，表单传递是字符流，不能传递二进制流，通过设置表单的enctype属性传递复合数据.

enctype的属性

```text
1. application/x-www-form-urlencoded：【默认】，表示传递的是带格式的文本数据。
2. multipart/form-data：复合的表单数据（字符串，文件），文件上传必须设置此值
3. text/plain：用于向服务器传递无格式的文本数据，主要用户电子邮件
```

2.服务器接收文件

```text
超全局变量#_FILES是一个二维数组,用来保存客户端上传到服务器的文件信息. 二维数组的行是文件域的名称. 有5个
1. $_FILES[]['name']: 上传的文件名
2. $_FILES[]['type']: 上传文件的类型, 类型为MIME类型(image/jpeg, image/gif, image/png)
3. $_FILES[]['size']: 上传文件的大小, 以字节为单位
4. $_FILES[]['tmp_name']: 文件上传的临时文件
5. $_FILES[]['error']: 错误编码(值有0,1,2,3,4,6,7) 0表示正确
```

| 值   | 错误描述                                                     |
| ---- | ------------------------------------------------------------ |
| 0    | 正确                                                         |
| 1    | 文件大小超过了php.ini中允许的最大值    upload_max_filesize = 2M |
| 2    | 文件大小超过了表单允许的最大值                               |
| 3    | 只有部分文件上传                                             |
| 4    | 没有文件上传                                                 |
| 6    | 找不到临时文件                                               |
| 7    | 文件写入失败                                                 |

  注意: MAX_FILE_SIZE必须在文件域的上

3. 将上传文件移动到指定的位置

```php
函数:
	move_uploaded_file(临时文件, 目标地址);
```

```php+HTML
<body>
<?php
if(!empty($_POST)) {
	if($_FILES['face']['error']==0){  //上传正确
        //文件上传
		move_uploaded_file($_FILES['face']['tmp_name'],'./'.$_FILES['face']['name']);
	}else{
		echo '上传有误';
		echo '错误码:'.$_FILES['face']['error'];
	}
}
?>
<form method="post" action="" enctype='multipart/form-data'>
	<input type="file" name="face">
	<input type="submit" name="button" value="上传">
</form>
</body>
//上传的同名的文件会被覆盖
```

4.文件上传的相关配置

```text
post_max_size = 8M: 表单允许的最大值
upload_max_filesize = 2M: 允许上传的文件大小
upload_tmp_dir =F:\wamp\tmp：指定临时文件地址，如果不知道操作系统指定
file_uploads = On：是否允许文件上传
max_file_uploads = 20：允许同时上传20个文件
```

5.更改文件名字

```php
//方法1: 通过时间戳做文件名
<?php
    $path='face.stu.jpg';
    //echo strrchr($path,'.');	//从最后一个点开始截取，一直截取到最后
    echo time().rand(100,999).strrchr($path,'.');

//方法2: 通过uniqid() 实现
<?php
    $path='face.stu.jpg';
    echo uniqid().strrchr($path,'.'),'<br>';   //生成唯一的ID
    echo uniqid('goods_').strrchr($path,'.'),'<br>';   //带有前缀
    echo uniqid('goods_',true).strrchr($path,'.'),'<br>';  //唯一ID+随机数
```

6.验证文件格式

```php
//方法1: 判断文件的扩展名(不能识别文件伪装)
<?php
    if(!empty($_POST)) {
	$allow=array('.jpg','.png','.gif');	//允许的扩展名
	$ext=strrchr($_FILES['face']['name'],'.');  //上传文件扩展名
	if(in_array($ext,$allow))
		echo '允许上传';
	else
		echo '文件不合法';
    }
    ?>
    <form method="post" action="" enctype='multipart/form-data'>
        <input type="file" name="face">
        <input type="submit" name="button" value="上传">
    </form>
    </body>
 //注意：比较扩展名不能防止文件伪装。
---------------------------------------------------------------
//方法2: 通过$_FIELS[]['type']类型（不能识别文件伪装）
<body>
<?php
if(!empty($_POST)) {
	$allow=array('image/jpeg','image/png','image/gif');	//允许的类别
	$mime=$_FILES['face']['type'];  //上传文件类型
	if(in_array($mime,$allow))
		echo '允许上传';
	else
		echo '文件不合法';
}
?>
<form method="post" action="" enctype='multipart/form-data'>
	<input type="file" name="face">
	<input type="submit" name="button" value="上传">
</form>
</body>
//注意：比较$_FIELS[]['type']不能防止文件伪装。
---------------------------------------------------------------
//方法3: php_fileinfo扩展（可以防止文件伪装）
在php.ini中开启fileinfo扩展
   extension=php_fileinfo.dll
<body>
<?php
    if(!empty($_POST)) {
        //第一步：创建finfo资源
        $info=finfo_open(FILEINFO_MIME_TYPE);
        //var_dump($info);		//resource(2) of type (file_info) 
        //第二步：将finfo资源和文件做比较
        $mime=finfo_file($info,$_FILES['face']['tmp_name']);
        //第三步，比较是否合法
        $allow=array('image/jpeg','image/png','image/gif');	//允许的类别
        echo in_array($mime,$allow)?'合法':'不合法';
    }
    ?>
    <form method="post" action="" enctype='multipart/form-data'>
        <input type="file" name="face">
        <input type="submit" name="button" value="上传">
    </form>
    </body>
```

小结：验证文件格式有三种方法

1、可以验证扩展名（不可以防止文件伪装）

2、通过`$_FILES[]['type']`验证（不可以防止文件伪装）

3、通过file_info扩展（可以防止文件伪装）



7.完整的文件上传

第一步：验证是否有误

第二步：验证格式

第三步：验证大小

第四步：验证是否是http上传

第五步：上传实现

```php
<body>
<?php
/**
*验证错误
*如果有错，就返回错误，如果没错，就返回null
*/
function check($file) {
	//1：验证是否有误
	if($file['error']!=0){
		switch($file['error']) {
			case 1:
				return '文件大小超过了php.ini中允许的最大值,最大值是：'.ini_get('upload_max_filesize');
			case 2:
				return '文件大小超过了表单允许的最大值';
			case 3:
				return '只有部分文件上传';
			case 4:
				return '没有文件上传';
			case 6:
				return '找不到临时文件';
			case 7:
				return '文件写入失败';
			default:
				return '未知错误';
		}
	}
	//2、验证格式
	$info=finfo_open(FILEINFO_MIME_TYPE);
	$mime=finfo_file($info,$file['tmp_name']);
	$allow=array('image/jpeg','image/png','image/gif');	//允许的类别
	if(!in_array($mime,$allow)){
		return '只能上传'.implode(',',$allow).'格式';
	}
	//3、验证大小
	$size=123456789;
	if($file['size']>$size){
		return '文件大小不能超过'.number_format($size/1024,1).'K';
	}
	//4、验证是否是http上传
	if(!is_uploaded_file($file['tmp_name']))
		return '文件不是HTTP POST上传的<br>';

	return null;  //没有错误
}

//表单提交
if(!empty($_POST)) {
	//上传文件过程中有错误就显示错误
	if($error=check($_FILES['face'])){
		echo $error;
	}else{
		//文件上传，上传的文件保存到当天的文件夹中
		$foldername=date('Y-m-d');		//文件夹名称
		$folderpath="./uploads/{$foldername}";	//文件夹路径
		if(!is_dir($folderpath))
			mkdir($folderpath);
		$filename=uniqid('',true).strrchr($_FILES['face']['name'],'.');	//文件名
		$filepath="$folderpath/$filename";	//文件路径
		if(move_uploaded_file($_FILES['face']['tmp_name'],$filepath))
			echo "上传成功,路径是：{$foldername}/{$filename}";
		else
			echo '上传失败<br>';
	}

}
?>
<form method="post" action="" enctype='multipart/form-data'>
	<input type="file" name="face">
	<input type="submit" name="button" value="上传">
</form>
</body>
```

8.时间戳转换格式

```php
echo date('Y-m-d H:i:s',1231346),'<br>';//将时间戳转成年-月-日 小时:分钟:秒
echo date('Y-m-d H:i:s'),'<br>';	//将当前的时间转成年-月-日 小时:分钟:秒

-----------------------------------------------------------------
设置时区（php.ini）
;http://php.net/data.timezone
data.timezone = "PRC";
```

# 数据库

数据库相关知识:

```
1. 数据库：数据库中存放的是表，一个数据库中可以存放多个表
2. 表：表是用来存放数据的。
3. 关系：两个表的公共字段
4. 行：也称记录，也称实体
5. 列：也称字段，也称属性
6.数据冗余：相同的数据存储在不同的地方; 冗余只能减少，不能杜绝。
减少冗余的方法是分表
7.数据完整性：正确性+准确性=数据完整性
```



## 	1.MySQL的基本操作

### 1.1进入数据库的方式

```mysql
1.mysql -uroot -proot  格式: mysql -u帐号　-p密码
	C:\Windows\system32>mysql -uroot -proot
2.mysql -uroot -p 回车提示输入密码
	C:\Windows\system32>mysql -uroot -p
	Enter password: *****
```

### 1.2 查看mysql的所有数据库

​	一般固定单词命令是大写

```mysql
SHOW DATABASES;
    mysql> SHOW DATABASES;
    +--------------------+
    | Database           |
    +--------------------+
    | information_schema |
    | mydb               |
    | mysql              |
    | performance_schema |
    | sys                |
    +--------------------+
    5 rows in set (0.00 sec)
```

### 1.3 创建名为test的数据库

```mysql
create database test;格式: create database 数据库名
	mysql> create database test;
	Query OK, 1 row affected (0.00 sec)
```

```mysql
create table [if not exists] `表名`(
    `字段名` 数据类型 [null|not null] [default] [auto_increment] [primary key] [comment],
    `字段名 数据类型 …
)[engine=存储引擎] [charset=字符编码]

null|not null     是否为空
default:          默认值
auto_increment    自动增长,默认从1开始，每次递增1
primary key       主键，主键的值不能重复，不能为空,每个表必须只能有一个主键
comment:          备注
engine            引擎决定了数据的存储和查找   myisam、innodb

脚下留心：表名和字段名如果用了关键字，要用反引号引起来。
```

### 1.4 删除名为test的数据库

```mysql
drop database test;		格式: drop database 数据库名;
    mysql> drop database test;
    Query OK, 0 rows affected (0.00 sec)
```

## 2.MySQL的基本操作

​		mysql中保存了很多数据库、一个数据库中可以保存很多表。对数据表的增(创建表) 删(删除表) 改(修改表字段)查(查询表结构)。  注意：这里的操作对象是表，对表的操作也就是表的结构，和表中的字段的操作(字段和记录要分清楚)  前提：表是在数据库下的，所以要先确实使用哪个数据库。

​	数据库表的文件

```mysql
一个数据库对应一个文件夹
一个表对应一个或多个文件
引擎是myisam，一个表对应三个文件
	.frm	：存储的是表结构
	.myd	:存储的是表数据
	.myi	:存储的表数据的索引
引擎是innodb,一个表对应一个表结构文件，innodb的都有表的数据都保存在ibdata1文件中，如果数据量很大，会自动的创建ibdata2，ibdata3...
```

innnodb和myisam的区别

| 引擎   |                                                              |
| ------ | ------------------------------------------------------------ |
| myisam | 1、查询速度快<br />2、容易产生碎片<br />3、不能约束数据      |
| innodb | 1、以前没有myisam查询速度快，现在已经提速了<br />2、不产生碎片<br />3、可以约束数据 |

脚下留心：推荐使用innodb。

复制表

```
语法一：create table 新表 select 字段 from 旧表
特点：不能复制父表的键，能够复制父表的数据

语法二：create table 新表 like 旧表
特点：只能复制表结构，不能复制表数据
```



### 2.1.使用表

```mysql
use test;		//use数据库表名
	mysql> use test;
	Database changed
```

### 2.2 创建数据表

```mysql
创建数据表格式
    create table 数据库表名 (
        字段名1	数据类型[列级别约束条件],
        字段名2	数据类型[列级别约束条件],
        字段名3	数据类型[列级别约束条件]
     );
解释: 
	1.[]中的内容表示可有可无,
	2.列级别这个“列”一定要搞清楚说的是什么，一张表中有行有列，列表示竖，行表示横
	3.约束条件

mysql> create table test(
    id int(11),
    name varchar(20),
    age int(11)
);
	Query OK, 0 rows affected (0.01 sec)
```

### 2.3创建有约束的表

​	六大约束: 主键约束, 外键约束, 非空约束, 唯一约束, 默认约束, 自动增加

#### 1.主键约束:

```mysql
	primary key: 独一无二(唯一) 和不能为空(非空),在表中增加记录,在该字段下的数据不能重复,不能为空
	一般被主键约束了的字段度习惯性的称该字段为该表的主键.
方式一:
    create table test(
        id int(11) primary key,
        name varchar(12),
        age int(11)
    );
方式二:
	create table test(
    	in int(11),
        name varchar(12),
        age int(11),
        primary key(id)
   	);
------------------------------------------------------------------
1.1多字段主键约束(复合)
	id和name都设主键，说明在以后增加的插入记录中，id和name不能同时一样，比如说。一条记录为id=1，name=yyy、另一条记录为：id=1，name=zzz。 这样是可以的。并不是你们所理解的两个字段分别度不可以相同。
方式一:
	create table test(
        id int(11) primark key,
        name varchar(12) primark key,
        age int(11)
);
方式二:
	create table test(
        id int(11),
        name varchar(12),
        age int(11),
        primary key(id,name);
);

删除主键约束: alert table 表名 drop primary key;
添加主键约束: alert table 表名 add primary key;
修改主键约束: alert table 表名 modify 字段名 字段类型 primary key;
```

#### 2.外键约束

​		有两张表，一张表是emp(员工)表，另一张表是dept(部门)表，一个员工属于一个部门，如何通过员工知道在哪个部门呢？那就只能在员工表中增加一个字段，能代表员工所在的部门，该字段只能存储dept中的主键了(因为主键是唯一的，才能确实是哪个部门，进而代表员工所在的部门，如果是部门名称，有些部门的名称可能是同名。就不能区分了。)，像这样的字段，就符合外键的特点，就可以使用外键约束，使该字段只能够存储另一张表的主键。如果不被外键约束，那么该字段就无法保证存储进来的值就一定是另一张表的主键值。

​		外键约束的特点:

```
1.外键约束可以描述任意一个字段(包括主键)，可以为空，并且一个表中可以有多个外键。但是外键字段中的值必须是另一张表中的主键。

2.这样被外键关联的两种表的关系可以称为父子表或者主从表。子表(从表)拥有外键字段的表，父表(主表)被外键字段所指向的表。

3.子表被外键约束修饰的字段必须和父表的主键字段的类型一样。
```

​		注意：一个表中有被外键修饰的字段，就称该表有外键(是“有外键”。而不是“是外键”)，并会给该表中的外键约束取一个名称，所以我们常说的这个表有没有外键，指的不是被外键约束修饰的字段名，而是指这个表是否有存在外键约束。也就是说，不能说这个表的外键是xxx(该表中被外键约束修饰的字段名)，这种说法是错误的，但是大多数人已经习惯了这样，虽然影响不大，但是在很多时候需要理解一个东西时，会造成一定的困扰。

格式:constraint		外键名称: 	foreign key(被外键约束的字段名称)

​								 主表名: references (主键字段)

```mysql
crete table testA(
	id int(1),
    name varchar(22),
    primary key(id)
);
create table testB(
	id int(11),
    name varchar(22) not null,
    primary key(id),
    constraint test1_test2_1 foreigh key(deptid) references tableA(id)
);
解释：tableB中有一个名为tableA_tableB_1的外键关联了tableA和tableB两个表，被外键约束修饰的字段为tableB中的deptId，主键字段为testA中的id　　　　　　
```

#### 3.非空约束

​		not null , 被该约束 修饰了的字段,就不能为空, 主键约束中就包括了这个约束

```mysql
create table test(
	id int(11),
    name varchar(22) not null,
    primary key(id)
);
```

#### 4.唯一约束

​		unique被唯一约束修饰了的字段, 表示该字段中的值唯一,不能有相同的值, 比如插入两条数据, 这两条数据中处于该字段的值不能是一样的

```mysql
create table test(
	id int(11),
    name varchar(22) unique,
    primary key(id)
);

//在插入的数据中, name值不能是一样的
```

#### 5.默认约束

​		default 指这一列的默认值是多少  比如，男性同学比较多，性别就可以设置为默认男，如果插入一行记录时，性别没有填，那么就默认加上男

```mysql
create table test(
	id int(11),
    name varchar(22) not null,
    cId int(11) default 11
);
```

#### 6.自动增加

​		AUTO_INCREMENT 一个表只能一个字段使用AUTO_INCREMENT，并且使用这个约束的字段只能是整数类型(任意的整数类型     TINYINT,SMALLIN,INT,BIGINT)，默认值是1，也就是说从1开始增加的。一般就是给主键使用的，自动增加，使每个主键的值度不一样，并且不用我们自己管理，让主键自己自动生成

```mysql
create table test(
	id int(11) primary key auto_increment,
    name varchar(22) not null
);
```

### 2.4 查询表结构

#### 2.4.1查看表基本结构语句

格式: describe 表名 / desc 表名 功能是一样的

```mysql
mysql> desc test_user;
+-------+-------------+------+-----+---------+----------------+
| Field | Type        | Null | Key | Default | Extra          |
+-------+-------------+------+-----+---------+----------------+
| id    | int(11)     | NO   | PRI | NULL    | auto_increment |
| name  | varchar(15) | YES  |     | NULL    |                |
| age   | int(2)      | YES  |     | NULL    |                |
+-------+-------------+------+-----+---------+----------------+
3 rows in set (0.00 sec)
```

#### 2.4.2 查看创建表语句

格式: show create table 表名

```mysql
mysql> show create table test_user;
+-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Table     | Create Table                                                                                                                                                                                   |
+-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| test_user | CREATE TABLE `test_user` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(15) DEFAULT NULL,
  `age` int(2) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1 |
+-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)
```

​	因为格式不好看, 可以切换为竖着查看

格式; show create table 表名\G;

```mysql
mysql> show create table test_user\G;
*************************** 1. row ***************************
       Table: test_user
Create Table: CREATE TABLE `test_user` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(15) DEFAULT NULL,
  `age` int(2) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1
1 row in set (0.00 sec)
```

### 2.5 修改数据表

修改数据表包括：对表中字段的增加、删除、修改。  在这个里面用的关键字为 alter

#### 2.5.1 修改表名

格式: alter table 旧表名 rename [to] 新表名;

```mysql
mysql> alter table test_user rename to user;
Query OK, 0 rows affected (0.00 sec)

--修改后
mysql> show tables;
+----------------+
| Tables_in_test |
+----------------+
| aitmy          |
| user           |
+----------------+
```

#### 2.5.2 修改表的字段名

格式: aleter table 表名 change 旧字段 新字段 新数据类型

```mysql
mysql> alter table user change name username varchar(22);
Query OK, 0 rows affected (0.01 sec)

--修改后
mysql> desc user;
+----------+-------------+------+-----+---------+----------------+
| Field    | Type        | Null | Key | Default | Extra          |
+----------+-------------+------+-----+---------+----------------+
| id       | int(11)     | NO   | PRI | NULL    | auto_increment |
| username | varchar(22) | YES  |     | NULL    |                |
| age      | int(2)      | YES  |     | NULL    |                |
+----------+-------------+------+-----+---------+----------------+
```

注意: 这个不仅能改变字段名字, 还能将字段的数据类型一并修改.

#### 2.5.3 修改表的数据类型

格式: alter  table 表名 modify 字段名 数据类型

```mysql
mysql> alter table user modify username varchar(20);
Query OK, 0 rows affected (0.01 sec)

-- 修改后
mysql> desc user;
+----------+-------------+------+-----+---------+----------------+
| Field    | Type        | Null | Key | Default | Extra          |
+----------+-------------+------+-----+---------+----------------+
| id       | int(11)     | NO   | PRI | NULL    | auto_increment |
| username | varchar(20) | YES  |     | NULL    |                |
| age      | int(2)      | YES  |     | NULL    |                |
+----------+-------------+------+-----+---------+----------------+
```

​		注意: 只能修改字段名的数据类型, 但是原理和change做的事情是一样的,但只能修改数据类型

#### 2.5.4 修改字段的排列顺序

格式1: alter table 表名 modify 字段1 数据类型 first/after 字段2

​	解释: 将字段1的位置放在第一,或者放到指定字段2的后面

格式2: alter tabe 表名 change 字段1 字段2 数据类型 first/after 字段3

​	解释：是将字段2覆盖字段1，然后在进行排序

```mysql
mysql> alter table user modify age int(2) after id;
Query OK, 0 rows affected (0.01 sec)

--修改后
mysql> desc user;
+----------+-------------+------+-----+---------+----------------+
| Field    | Type        | Null | Key | Default | Extra          |
+----------+-------------+------+-----+---------+----------------+
| id       | int(11)     | NO   | PRI | NULL    | auto_increment |
| age      | int(2)      | YES  |     | NULL    |                |
| username | varchar(20) | YES  |     | NULL    |                |
+----------+-------------+------+-----+---------+----------------+
```

#### 2.5.5 添加字段

格式: alter table 表名 add 新字段名 数据类型 [约束条件] [first/after 已存在的表名]

```mysql
mysql> alter table user add sex int (11);
Query OK, 0 rows affected (0.01 sec)

--添加后
mysql> desc user;
+----------+-------------+------+-----+---------+----------------+
| Field    | Type        | Null | Key | Default | Extra          |
+----------+-------------+------+-----+---------+----------------+
| id       | int(11)     | NO   | PRI | NULL    | auto_increment |
| age      | int(2)      | YES  |     | NULL    |                |
| username | varchar(20) | YES  |     | NULL    |                |
| sex      | int(11)     | YES  |     | NULL    |                |
+----------+-------------+------+-----+---------+----------------+
```

解释：在一个特定位置增加一个新的字段，如果不指定位置，默认是最后一个。

#### 2.5.6 删除字段

 格式: alter table 表名 drop 字段名;

```mysql
mysql> alter table user drop sex;
Query OK, 0 rows affected (0.01 sec)

--删除后
mysql> desc user;
+----------+-------------+------+-----+---------+----------------+
| Field    | Type        | Null | Key | Default | Extra          |
+----------+-------------+------+-----+---------+----------------+
| id       | int(11)     | NO   | PRI | NULL    | auto_increment |
| age      | int(2)      | YES  |     | NULL    |                |
| username | varchar(20) | YES  |     | NULL    |                |
+----------+-------------+------+-----+---------+----------------+
```

#### 2.5.7  删除表的外键约束

格式: alter table 表名 drop  foreign key 外键约束名

注意：外键约束名 指的不是被外键约束修饰的字段名，切记，而是我们在创建外键约束关系时取的名字。

#### 2.5.8 更改表的储存引擎

格式: alter table  表名 engine=更改后的储存引擎名

#### 2.5.9 删除表

格式: drop table 表名



删除被其他表关联的主表

```
	这个是比较重要的一点，在有外键关联关系的两张表中，如果删除主表，那么是删不掉的，并且会报错。因为有张表依赖于他。那怎么办呢？针对这种情况，总共有两种方法
　　1、先删除你子表，然后在删除父表，这样就达到了删除父表的目的，但是子表也要被删除
　　2、先解除外键关系，然后在删除父表，这样也能达到目的，并且保留了子表，只删除我们不需要的父表。在3.7中就讲解了如何删除外键关系
```

## 3.MySQL数据操作

### 1.插入数据

格式: insert into 表名 (字段名1, 字段名2....) values (值1, 值2...);

```mysql
写法一:
	mysql> insert into user (id,stuname,sex,`add`) values (1,'tom','男','北京');
------------------------------------------------------------
写法二: 
	mysql> insert into test (id,stuname) values (2,'berry');
------------------------------------------------------------
写法三:
	mysql> insert into stu(sex,`add`,id,stuname) values ('女','上海',3,'ketty');
------------------------------------------------------------
写法四:
	-- 插入字段名可以省略
	mysql> insert into stu values(4,'rose','女','重庆');
------------------------------------------------------------
	--插入默认值和空值
mysql> insert into stu values (5,'jake',null,default);

------------------------------------------------------------
	--插入多条数据
mysql> insert into stu values (6,'李白','男','四川'),(7,'杜甫','男','湖北');
```

### 2.更新数据

格式: update 表名 set 字段=值 [where 条件]

```mysql
update test set sex='女' where username='admin';
```

### 3.删除数据

格式: delete from 表名 [where 表名]

```mysql
delete form test where id=1;

//删除所有数据
delete from test;
```

delete from 表和truncate table 表区别？

```test
1、delete from 表：遍历表记录，一条一条的删除
2、truncate table：将原表销毁，再创建一个同结构的新表。就清空表而言，这种方法效率高。
```

### 4.查询数据

格式: select 字段名 from 表名

```mysql
--查询id字段的值
select id from test;

--查询多个字段的值
select id,username from test;

--查询所有字段的值
select * from test;
```

## 4.MySQL的数据类型

mysql中的数据类型是强类型

mysql的数据类型: 分别为数值型, 字符串型,  

​	

 













1、插入字段名的顺序和数据表中字段名的顺序可以不一致
2、插入值的个数、顺序必须和插入字段名的个数、顺序要一致。
3、如果插入的值的顺序和个数与表字段的顺序个数一致，插入字段可以省略







PHP函数整理

```
rand(1, 10); 获取1-10的随机数
define(); 定义常量
bccomp();	0:相等; 左边大返回1; 右边大返回-1
```



