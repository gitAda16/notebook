# line-height和vertical-algin

## 1、line-height由什么来决定

1 设置line-height属性

block

设置block中的行级元素的line-height，子元素会继承父级设置的line-height	

inline

设置自身元素的line-height

2 不设置line-height属性 

line-height属性只对行级元素有效,如果行级元素没有设置，则他的line-height是由内容来决定的

em-square 为相对单位，ascender decender line-gap都为相对em-square的高度

line-height = font-size/em-square*(ascender+descender+line-gap)

同时这个高度也是line-height:normal的计算方法

## 2、vertical-align是相对于谁来对齐的

相对于父级元素的对应位置来对齐的

父级元素的 top/bottom 是line-height中行的最上面/最下面的地方，如果父级设置了line-height，就不用说了，如果没有设置，就是子元素中最大的line-height



父级元素是block 没有设置line-height，那么父级中的子元素的line-height默认为子元素的最大line-height，确切的来说是最高到最低才是line-height

示例

```css
.pa{
            background-color: yellow;
            font-size: 40px;
        }
        .pa .line{
            vertical-align: baseline;
            font-size: 16px;
        }
        .pa .line1{
            font-size: 60px;
            vertical-align: middle;
        }
        .pa span{
            border:1px solid blue;
        }
        .sh{
            display: inline-block;
            width:40px;
            background-color: red;
            height:auto;
        }
```



```html
<div class="pa">
            <img class="line" src="trees/ph1.jpg" alt="">
            <span class="line">我是小span</span>我是父级pf
            <span class="sh"></span>
            <span class="line1">我是大span</span>
        </div>
```

里面的元素都是相对于“我是父级pf” 来对齐的

参考https://zhuanlan.zhihu.com/p/25808995