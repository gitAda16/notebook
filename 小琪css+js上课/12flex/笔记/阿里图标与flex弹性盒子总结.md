# 矢量图标 字体

优点：

字体比图片快

字体可以改变大小颜色 很方便

## 阿里图标：

unicode(推荐 ie6+都可以使用)

font-class（ie8）

symbol

依次兼容性变小

字体样式对阿里图标生效

## flex 弹性盒子

是一种布局，可以使容器内的元素按照横向排列或者竖向排列，同时容器内的元素会按照一定策略自动填满容器或者缩小以免超出容器 

可以通过设置display:flex得到弹性盒子，弹性盒子中的第一级子元素即为弹性元素 flex items

### 相关属性

**flex-direction**

定义了弹性盒子里面的元素的排列主轴（justify-content），以及排列的方向

row:(默认) 横向排列，和文档内容顺序一致

row-reverse: 横向排列，和文档内容顺序相反

column:竖向排列，和文档内容顺序一致

column-reverse:竖向排列，和文档内容顺序相反

**justify-content**

定义元素在主轴方向上的布局

center:元素位于主轴中间

start:元素位于主轴开始位置

end:元素位于主轴结束位置

space-between: 元素在主轴方向平均分布，其中两端元素会紧贴父级盒子的两端

space-around:元素在主轴方向平均分布,两端元素离父级元素的间距为元素间距的一半

space-evenly:元素在主轴方向平均分布

**align-items**

定义了元素在交叉轴方向的布局

normal:（默认）不同的元素有不同的影响，如 弹性元素会表现为stretch，具体情况用的时候再去了解了

strech:会在交叉轴的方向上延伸

center:元素位于交叉轴的中间

start:元素位于交叉轴的开始位置

end:元素位于交叉轴的结束位置

baseline:和基线对齐

**flex-wrap**