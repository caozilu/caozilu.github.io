---
layout: post
title:  "编程基础：基本原理"
date:   2016-09-25
---
![foundations-of-programming-fundamentals](/images/ff8eafe371c56c65ddc4d660cac91b2a.jpeg)

[Foundations of Programming: Fundamentals](https://www.lynda.com/JavaScript-tutorials/Foundations-of-Programming-Fundamentals/83603-2.html)

* table of contents
{:toc}

# 简介

编程是一项强大的技能。许多人对编程看似复杂的概念、深不可测的原理望而却步，只有一小部分人仍然保持着强烈的好奇心和不罢休的求知欲，于是他们从千千万万个程序的使用者中脱颖而出成为程序的开发者。

# 基本概念

计算机程序由一系列人类交给计算机处理的指令组成，如计算2+3的结果，在屏幕上显示字母Y，判断用户是否敲击了空格键，让屏幕上的某个像素点显示白色。编程语言是人类向计算机表达指令的方式。计算机CPU只懂得机器代码，为了弥补机器和人类认知之间的鸿沟，人类发明了由低级到高级的数百种编程语言，最终都转换成可执行的机器代码。通常所说的编程，则是由程序员使用较为高级的编程语言，在编辑器或IDE中编写符合该语言语法的语句。

编程语言分为编译语言和直译语言。编译语言经过编译器先行编译为机器代码，之后再运行。直译语言通过解释器（如JavaScript引擎）动态将代码逐句直译为机器代码，之后再运行。

# 本教程的示范语言

JavaScript是一门C语言风格的直译语言。有如俄罗斯套娃般，它运行在计算机中的操作系统中的浏览器中的网页上，因此被称作脚本语言。本教程暂不考虑JavaScript在服务端运行的情况。

# 语言基础

#### 存储数据

计算机程序处理数据（如整数、小数、字符、字符串、布尔值等不同类型的数据）。在编程语言中，变量作为容器，储存不断变化的数据，本质是在计算机内存中划出一小块。强类型的语言要求在创建变量时指定数据类型，防止变量的值发生数据类型的变化而引发程序崩溃。JavaScript属于弱类型语言，其变量可保存的数据不限制为固定的类型。

{% highlight javascript %}
//创建变量year, 其值为数字2016
var year = 2016;
//创建变量message, 其值为字符串Hello, world
var message = "Hello, world";
{% endhighlight %}

> 操作符：=为变量赋值，+、-、\*、/为算术运算符，++、--表示当前变量的值+1或-1，+=、-=、\*=、/=表示将当前变量运算后的值再赋给这一变量。

#### 添加条件

通常，计算机程序是从上到下逐行运行的。条件语句则为一部分代码是否执行添加了限制条件，如JavaScript中的if、if/else、switch语句。

{% highlight javascript %}
var a = 5;
var b = 10;

if ( a < b ) {
  alert("a小于b");//a小于b时才会执行
}//否则继续执行下面的代码
{% endhighlight %}

> 操作符：==表示值相等，===表示值相等，数据类型也相同，即全等。!=、!==分别对应不相等和不全等。>、<、>=、<=用于比较大小。&&、\|\|表示逻辑与、逻辑或。

#### 组织代码

将一些语句组合成可重复使用的函数，是计算机程序中有效的代码组织方式。函数可以接收参数，也可以返回其中代码的执行结果，成为程序中既可输入又可输出的功能片段。创建函数将形成对应的作用域，将函数内的语句与函数外区分开，产生局部变量和全局变量的差异。

{% highlight javascript %}
//函数声明
function addTwoNumbers(a, b) {
  var result = a + b;
  return result;
}

//调用函数
addTwoNumbers(5, 10);
{% endhighlight %}

程序亦可拆分成不同的文件。将程序拆分成相互独立又相互依赖的模块的作法称为模块化编程，是一种广泛应用的程序设计思想。

#### 避免重复

程序中经常需要重复某些操作，与其重复代码，不如告诉计算机相应的边界条件让其自动执行。while语句在符合条件时能够重复执行相应代码，形成循环。当变量的值不再满足条件时，程序将跳出循环，继续执行之后的代码。

{% highlight javascript %}
var a = 0;

while ( a < 5 ) {
  alert(a);
  a++;
}//当a的值为0、1、2、3、4时，执行{}中代码，否则跳出循环继续执行下面的代码
{% endhighlight %}

将while语句的起止条件集合在一起便构成了常用的for循环。

{% highlight javascript %}
for (var i = 0; i < 5; i++) {
  //要重复执行的代码
}
{% endhighlight %}

#### 匹配模式

计算机程序中常常需要验证数据。几乎所有的编程语言都内建正则表达式的功能，用来验证给定的字符串是否符合某一格式：是否为email地址、URL，是否符合密码设定的规则，是否为有效的身份证号码和银行卡号。

{% highlight javascript %}
//一个email正则表达式
/^[a-zA-Z0-9._-]+@([a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/
{% endhighlight %}

#### 数据集合

将一些需要集中管理的数据放到一起，组成数据集合，是计算机程序中常见的数据结构。JavaScript中采用数组实现这一功能，从0开始用整数为其中的数据编号，并提供一系列操作其中数据的方法（对象的变量称为属性，函数称为方法）。

{% highlight javascript %}
var fruits = ["Apple", "Banana"];

alert(fruits.length);//数组长度为2
var first = fruits[0];//取得数组第1个元素，即Apple
var newLength = fruits.push("Orange");//将Orange添加至原数组末尾，返回新数组的长度。数组变为["Apple", "Banana", "Orange"]
var last = fruits.pop(); //去掉原数组末尾的元素，并返回去掉的元素Orange。数组变为["Apple", "Banana"]
{% endhighlight %}

不同的编程语言对数据集合有不同的实现。许多语言中，一个数据集合只能储存同一类型的数据，而在JavaScript中，一个数组可以储存不同类型的数据。不以数字来编号，而以一个独一无二的key来标记集合中的数据，形成若干组键值对，这便构成关联数组、映射、符号表、字典。

# 编码规范

代码编写方式有如一家报纸的行文风格。在项目开始前，约定好变量和函数的命名方式、代码缩进、语句结束必须加分号、函数必须先声明再调用等，有助于项目的统一管理和项目质量的提高。

{% highlight javascript %}
//驼峰命名法
var highScore;
function calculateDistance();
{% endhighlight %}

# 输入与输出

程序的本质就是输入与输出。早期的程序都是批处理：把完整的程序交给计算机运行，完成之后得到结果。如今，程序尤其是有图形界面的软件更多与用户进行交互，用户的操作改变程序的输入，并得到相应的结果，这是一种被称为事件驱动程序设计的思想。通常，程序在计算机内存中运行，运行结果保存在计算机硬盘中，称为程序的状态的持久化。

JavaScript程序的输入与输出主要发生在对DOM（文本对象模型，将网页上的元素抽象为分层次、有结构的数据）的读取与写入。JavaScript内建事件机制，来完成网页上的交互：预先定义一系列事件侦听函数（通常以on开头，如onclick），当网页上发生用户点击鼠标、键盘输入等事件时，触发相应的侦听函数（或称事件处理函数）。

{% highlight javascript %}
var elem = document.getElementById("heading1");//读取网页上id为heading1的元素
elem.onclick = function() {//当点击heading1时执行
  elem.innerHTML = "标题1";//写入元素的内容为标题1
};
{% endhighlight %}

当数据以文件的形式存储在计算机硬盘中时，读取和写入文件称为文件I/O。在各种编程语言中的实现大同小异。流I/O用来表示从计算机硬盘之外的媒介读取和写入数据。

{% highlight ruby %}
#使用ruby读取文件
f = File.open("example.txt", "r")#以只读模式打开文件
f.each_line do { |line|
  puts line#逐行读取文件
}
f.close#关闭文件

#使用ruby写入文件
File.open("example.txt", 'w') {|f|#以写入模式打开文件
  f.write("your text")#写入文本
}
{% endhighlight %}

# 代码调试

完整的程序不是一蹴而就的。计算机严格执行代码，但人难免会有疏忽和糊涂。为了防止拼写错误和逻辑错误，各种编程语言都内建错误处理功能，各类开发工具也具备错误提示和代码调试功能。开发人员可以通过调试工具逐步运行代码，定位异常，检查变量的值是否正确，函数的输出是否符合期望。

![debugger](/images/debugger.png)

# 面向对象编程

早期的程序是一系列从头执行到尾的步骤。面向对象编程这种程序设计思想则把这些步骤抽出来，封装成具有数据和逻辑的对象，对象与对象之间还能通信（交换数据）。把封装对象的规则抽象出来，成为具有属性和方法的类。对象是类的实例，能表示真实世界里的事物（如电商网站的买家、卖家、商品），又能反映计算机程序中的变量和函数。

一门完善的面向对象编程语言内建有许多常用的类，意味着在使用这门语言之前，已经有许多现成的属性和方法可供使用。JavaScript是一门松散的面向对象编程语言，内建有Array、RegExp、Date、Math等类似于类的实现。常见的面向对象编程语言还有Java, C++, C#, Python, PHP, Ruby, Perl, Objective-C, Swift等。

# 高级话题

创建变量和对象都需要占据计算机内存。低级语言需要在变量和对象使用完后手动清理内存，而高级语言通过引用计数和垃圾回收机制来管理内存，更为高级的语言则利用这些机制自动管理内存。

算法是指完成某一任务的一系列步骤。完成同一任务常常有多种方式，即多种算法。往往简单的算法容易写出，但性能较差；复杂的算法性能很好，但难以写出且很难维护。计算机编程便是这样一种在性能和优雅之间不断权衡的艺术。

{% highlight text %}
冒泡算法，算法从左至右运行，两两比较相邻的数字，大的在右，小的在左
给定数字排列3、5、2、4、1，要求从小到大排序
3 5 2 4 1
3 2 4 1 5
2 3 1 4 5
2 1 3 4 5
1 2 3 4 5
{% endhighlight %}

线程指计算机操作系统的最小运算维度。多线程指程序能同时占用多个线程执行。

# 主流编程语言一览

[![programming-languages](/images/which-programming-language-should-i-learn-first-infographic.png)](http://carlcheo.com/wp-content/uploads/2014/12/which-programming-language-should-i-learn-first-pdf.pdf)

编程语言的数量成百上千，但主流的只有寥寥几种。如同人类世界的各国语言，编程语言之间的特性不尽相同。有的是编译语言，有的是直译语言；有的面向对象，有的不是；有的是强类型语言，有的是弱类型语言；有的是某一领域的专门语言，有的是全功能的通用语言……编程语言之间也相互借鉴，许多语言都是由C语言发展而来，不同编程语言的特性、内置功能甚至设计思想都大同小异。

C
{% highlight c %}
#include <stdio.h>

int main(void)
{
    printf("hello, world\n");
}
{% endhighlight %}

Java
{% highlight java %}
class HelloWorldApp {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
{% endhighlight %}

C#
{% highlight c# %}
using System;

class Program
{
    static void Main(String[] args)
    {
        Console.WriteLine("Hello, world!");
    }
}
{% endhighlight %}

Ruby
{% highlight ruby %}
class String
    def say
        puts self
    end
end
'Hello, world!'.say
{% endhighlight %}

语言中没有内置、但实际开发中又普遍需要的功能，通常已经有人写好相关的代码，形成库或者框架。开发时可以直接引用，避免重复劳动。

# 结语

如同人类的语言在交流中演变，人类社会的工具在使用的过程中不断改进，想要熟练运用编程这一技能，关键在于实践。互联网上有无数有趣的开源项目和像你一样好奇的人，加入他们，get your hands dirty!
