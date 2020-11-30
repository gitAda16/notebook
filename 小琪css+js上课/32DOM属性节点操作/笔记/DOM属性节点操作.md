## 关于标签中的属性节点的操作

div 元素接单

class="" 属性节点

123 文本节点

可以通过元素对象直接访问到html定义过的属性

如果没有被html定义过的属性，是无法通过点访问到

元素.未定义属性=扩展了一个属性

```
<div ada="d" id="dd"></div>
console.log(dd.ada);
```

这三个方法可以获取到定义的或非定义的属性

getAttribute

setAttribute

removeAttribute



dataset

可以设置属性，属性格式：data-属性

如果是驼峰形式，驼峰会变成-

```
window.onload = function(){
boxDom.dataset.test="45";
                boxDom.dataset.keyWord="key";
                boxDom.onclick = function(){
                    // alert(boxDom.getAttribute("mo"));
                    alert(boxDom.dataset.mo);
                }
            }
<div data-mo="100" id="boxDom">12</div>
```

## 查找字符串

## 创建节点

document.createElement(); 创建元素节点

document.createTextNode();创建文本节点

parentNode.appendChild();追加节点到parentNode里面

先把元素从父元素摘除，再放到父元素中

```
var divDom = document.createElement("div");
                divDom.innerText="asd";
                divDom.style.cssText = "width:100px;height:100px;background-color:red;"
                document.body.appendChild(divDom);
```

parentNode.removeChild();删除节点，注意删除节点不能删除自己，只能找到父节点，再删除

## 位置大小属性

### 大小

offsetWidth = width+border+padding

offsetHeight

clientWidth = width+padding

clientHeight

scrollWidth = width+padding+scroll溢出的大小

scrollHeight

### 位置

offsetParent 获取定位父级

offsetLeft 获取相对定位父级的距离

offsetTop

