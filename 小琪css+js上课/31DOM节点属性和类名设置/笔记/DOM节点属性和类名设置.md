## DOM

### 节点的属性

#### 文本

innerText 读写 标签里的内容

textContent 读写 兼容问题 ie9以上 属于标准dom里面的东西

innerHTML 不属于标准dom，和innerText的区别，innerHTML可以解析标签

下面两个属性很少用

outerHTML  和innerHTML的区别，会获取到自身的标签内容，innerHTML只会获取孩子节点的标签内容

outerText  和innerText的区别，outerText在修改的时候，会把自身标签内容都改了，innerText只会修改孩子的内容

#### 样式

**style** css样式 获取的是行内样式 即标签中属性style定义的样式

复合属性的连字符要转换成驼峰的写法，如 margin-left=>marginLeft

style.cssText可以一次写多个样式，

style.cssText = “width:100px”会清空标签的style，然后写入新的样式，

style.cssText+=“width:100px” 不会情况原有样式，只会增加新样式

注意style设置的样式是写在标签里面的，这样样式的优先级会高于c外部引用的css样式表

style.cssFloat//用于非IE

style.styleFloat//IE

现在直接用style.float就可以了，都兼容

**获取行间行内样式**

currentStyle //节点的一个属性 用于IE

getComputedStyle(el，pseudo)//一个方法，获取某个元素的样式 用于ie9以上这个方法还可以获取伪元素

#### 添加样式

```
function css(el,attr,value){
  el.style[attr] = value;
}
function css1(el,cssObj){
  for(var k in cssObk){
    el.style[k] = cssObj[k]
  }
}
```



### 类名

#### 通过类名获取元素

getElementByClassName(); //ie9以上 只能获取单类名，如果有层级关系，获取不了

querySelectorAll//ie9以上

在节点中的属性，要获取标签的class属性，要使用className，这个属性可读写

```
var doc = document.getElementById("test");
doc.className="sd";
```

getElementByClassName的返回结果，每次读取，都会获取重新获取一遍结果

```
var d1 = document.getElementsByClassName)("red");
var d2 = document.querySelectorAll(".red");
for(var i=0,len = d1.length;i<len;i++){
if(d1[i].className="red"){
  d1[2].className="green"
}
}
```

getElementByClassName解决兼容问题

1 通过getElementsByTagName("*")获取到页面的所有标签

2 遍历里面的标签，将标签中的className为指定值的节点加入数组中

3 返回数组

#### 设置类名

```
function addClass(el,name){
  if(el.className.length>0){
    el.className+=" "+name;
  }else{
    el.className = name;
  }
}//这种处理方法会导致重复类名设置
function addClass(el,name){
  var arr = el.className.split(" ");
  var nameArr = name.split(" ");
  for(var i=0;i<arr.length;i++){
  	for(var j=0;j<nameArr.length;j++){
      if(nameArr[j]&&arr[i]==nameArr[j]){
        nameArr[j] = false;
      }
    }
  }
  for(var i=0;i<nameArr.length;i++){
    if(nameArr[i])
    arr.push(nameArr[i]);
  }
  
  el.className = arr.join(" ");
  new Set([])//可以吧数组转换成set
  Array.from可以吧set转换成array
  //还可以用h5 的 clasList.add 没有才添加，一次只能添加一个
  el.classList.add("sth")
}
```

#### 删除类名

```
function removeClass(el,name){
  var arr = el.className.split("");
  for(var i=0;i<arr.length;i++){
    if(arr[i].clasName==name){
      arr.splice(i,1);//有bug 会导致length改变
    }
  }
}
```

不要用background 或者a的href做判断

```
console.log(container.style.backgroundColor);
console.log(container2.style.backgroundColor);
console.log(a.href);
<div id="container" style="background-color: #333">
</div>
<div id="container2" style="background-color: red">
</div>
<a id="a" href="#"></a>
```

