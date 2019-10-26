# JS基本用法

## 什么是表达式和语句
~~~javascript
var i=1+2;
;;;
~~~
var i=1+2; 是一个语句，用";"表示结束。1 + 2 叫做表达式（expression），指一个为了得到返回值的计算式。语句和表达式的区别在于，前者主要为了进行某种操作，一般情况下不需要返回值；后者则是为了得到返回值，一定会返回一个值。

多个“;”表示多个语句，如果前面是空值表示空语句。
## 标识符的规则
标识符（identifier）指的是用来识别各种值的合法名称。a和A是两个不同的标识符。

第一个字符，可以是任意 Unicode 字母（包括英文字母和其他语言的字母），以及美元符号（$）和下划线（_）。
第二个字符及后面的字符，除了 Unicode 字母、美元符号和下划线，还可以用数字0-9。

~~~javascript
var arg0=0+1
var _underline=1+2
var $dolor=2+3
var π1=3+4
var 菜虚鲲=console.log('唱跳rap')
~~~
以上都是合理的。
## if else 语句
下面是标准的if else语句：
~~~JavaScript
var a=4
function fn(){
    if(a===1){
        console.log('a是1')
    }else if(a===2){
        console.log('a是2')
    }else{
        console.log('什么都没有')
    }
}

//"什么都没有"
~~~
if(布尔值){代码块}，如果代码块里只有一句话，可以省略{}。
~~~javascript
a=1
if(a===2)
    console.log('这句不会显示')
    console.log('a是1')
    
    //"a是1"  等同于
a=1
if(a===2){
    console.log('这句不会显示')
}
    console.log('a是1')    
~~~
下面是次要写法，但主张第一种标准写法；
~~~javascript
function fn(){
    if(){
        return 表达式
    }if(){
        return 表达式
    }if(){
        return 表达式
    }
}
~~~
一些特殊写法：
* switch 表达式
~~~javascript
var a=2
switch(a){
    case 1:
    case 3:
        console.log('单数')
        break;
    case 2:
    case 4:
        console.log('双数')
        break;
}
//"双数"
~~~
break是必须要写的，否者上下句会被当做是一个语句
* 冒号表达式
~~~JavaScript
function max(a,b){
    return a>b ? a:b
}

//等同于
function max(a,b){
    if(a>b) return a
    else return b
    }
}
~~~
* && 表达式
~~~javascript
if(window.Date){
    console.log('Date存在')
}
//"Date存在"  等同于
window.Date && console.log('Date存在')

// A&&B 如果A真则返回B的值，如果A假则直接返回A的值
~~~
* || 表达式
~~~javascript
if(a){
    a=a
}else{
    a=0 
}
//等同于
a= a||0

//x=A||B||C 取里面第一个真值，全假就取最后一个值
~~~

## while for 语句
* while循环
  
  while(条件){
      语句;
    }
~~~JavaScript
var a=1
while(a<10){
    console.log(a)
    a=a+1
}
~~~
但注意不要出现死循环了；
~~~javascript
var a=0.1
while(a !==1 ){
    console.log(a)
    a=a+0.1
}

//因为浮点数的存在，a得不到整数1，就会无限循环下去
~~~
* for循环
  
  for( 初始化表达式, 条件表达式, 递增表达式 ){ 语句; }

初始化表达式（initialize）：确定循环变量的初始值，只在循环开始时执行一次。

条件表达式（test）：每轮循环开始时，都要执行这个条件表达式，只有值为真，才继续进行循环。

递增表达式（increment）：每轮循环的最后一个操作，通常用来递增循环变量。
~~~javascript
var x = 3;
for (var i = 0; i < x; i++) {
  console.log(i);
}
// 0
// 1
// 2
~~~
for语句的三个部分（initialize、test、increment），可以省略任何一个，也可以全部省略。但三个部分都省略会导致无限循环。
~~~javascript
for ( ; ; ){
  console.log('无限循环');
}
~~~
## break continue
* break
~~~javascript
for(var a=0; a<5; a++){
    if(a%2===1){
        console.log(a)
        break
    }
}

//1
~~~
* continue
~~~javascript
for(var a=0; a<5; a++){
    if(a%2===1){
        console.log(a)
        continue
    }
}

//1
//3
~~~
## label标签
JavaScript 语言允许，语句的前面有标签（label），相当于定位符，用于跳转到程序的任意位置，标签的格式如下。

    label:
      语句
~~~javascript
foo:{
    console.log(1)
    break foo;
    console.log(2)
}
console.log(3)

//1
//3
~~~
break/continue也能配合标签使用。
