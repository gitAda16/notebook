## 什么是BFC

block formatting context

是css中盒子中的一种布局渲染方式，它规定了盒子中的block-level元素排列方式

注意bfc只是其中一种渲染方式

还有 inline formatting context

css3中有grid formatting context flex formatting context

**疑问**

1如果就写一个div，这个div中的normal flow 是什么formatting context?

2很多的网站都解释了什么情况下回生成BFG,那什么情况下又会生成LFC？



## BFC特性

1 不在同个bfc中的盒子垂直 marin不会叠加 同一个bfc的盒子垂直margin会相互抵消

2 具有bfc的盒子可以包含float元素，即计算bfc的高度时，浮动元素也参与计算

3 新建的bfc区域不会与floatbox叠加 

5 bfc是页面的一个隔离的独立容器，里面的子元素不会影响到外面，反之亦然

## 生成BFC的条件 一下任一条件满足即可

1 float不为none

2 position为absolute

3 不是block box的block container

4 block box 的overflow 是visible之外的值

**疑问**

对于block container的解释是只包含line box 或者 block box，那如果两者都包含是什么东东

## non-replaced vs replaced element

替换是指标签中的内容被外部资源替换，如<img src=""> img标签的内容由src定义，<iframe src> iframe中的内容，由src定义，都来自外部

常见的replaced element

1. audio
2. canvas
3. embed
4. iframe
5. img
6. math
7. object
8. svg
9. video
10. input