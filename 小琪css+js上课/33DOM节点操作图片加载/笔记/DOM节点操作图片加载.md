## dom

appendChild

removeChild

insertBefore 在已知节点前面插入一个节点，如果操作的是一个已经存在的节点，会将这个节点从原来的位置移除，再插入新的位置

parentNode.insertBefore(newNode, referenceNode) referenceNode必须是parentNode的子节点，如果referenceNode为null，则会在parentNode最后一个子节点后面插入newNode,这最后一个子节点包括匿名节点

```
var boxDom = document.getElementById("box");
                var p = document.createElement("p");
                p.innerText ="23";
                boxDom.insertBefore(p, boxDom.children[1]);
                <div id="box">
            <div>1</div>
            <div>2</div>
        </div>
```

cloneNode(boolean) 赋值节点 事件不会被复制

boolean 为true 深度克隆 子节点也会被克隆





窗口大小

chrome window.innerWidth window.innerHeight;

ie document.documentElement.clientWidht/document.documentElement.clientHeight

滚动条高度

document.documentELement.scrollTop

获取元素到可视窗口的距离

el.getBoundingClientRect(); ie不支持

## document的一些属性

document.all // 非标准 类型getElementsByTagName('*')

.title 获取页面标题

.body 返回body对象

.documentElement 返回文档对象

.documentElement.clientWidth/Height 视口大小

.documentElement.scrollTop/left 滚动条滚动位置

compatMode 判断浏览器页面是哪种渲染方式



## 上课练习

1 交换位置（非动态/动画）

2 图片加载