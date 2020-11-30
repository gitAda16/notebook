# string和number

## string

字符串是不可变的

属性

​	length

方法

charAt 获取索引位字符

charCodeAt 获取对应字符的ascii

String.fromCharCode 获取ascii对应的字符

substring(start,end)

substr(start,num)

slice

split 切割

indexof

lastIndexOf

replace

repeat //ie不兼容

includes//ie不兼容

## number

toFixed 转成对应精度的数字

toString 可以把数字转换成对应进制的字符

toLocalString

```
10.toFixed(1);//报错
10..toFixed(1);//后面的点会被解析成调用方法的点
10 .toFixed(1);
```

## Math数学方法

random 随机

sqrt 开方

abs 绝对值

sin(a) 正弦  a是弧度 如90度的弧度是 PI/2

cos 余弦

pow (n,m)  n^m

floor 向下取整 

向下取整位运算的做法：num|0    ~~num(取两次反)  num>>0 

ceil 向上取整

round 四舍五入

PI 圆周率 常量



wordpress 建站



