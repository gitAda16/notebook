# BootStrap

http://www.waibo.wang/bible/bootstrap3/html/2/2.2.1.html

## 环境配置

去官网下载BootStrap 3 (目前比较稳定的版本)

BootStrap依赖jquery，使用1.9以上的版本

BootStrap的目录

```
 bootstrap/
  ├── css/
  │   ├── bootstrap.css
  │   ├── bootstrap.min.css
  ├── js/
  │   ├── bootstrap.js
  │   ├── bootstrap.min.js
  └── img/
      ├── glyphicons-halflings.png
      └── glyphicons-halflings-white.png
```

然后引入对应的文件，示例如下

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Bootstrap 101 Template</title>
    <link href="bootstrap/css/bootstrap.min.css" rel="stylesheet" media="screen">
  </head>
  <body>
    <h1>Hello, world!</h1>
    <script src="jquery/jquery-1.12.4.min.js"></script>
    <script src="bootstrap-3.3.7-dist/js/bootstrap.min.js"></script>
  </body>
</html>
```

## 全局样式

### 排版 - 标题

标题(h1 ~ h6 / .h1 ~ h6)

副标题 (small)

```html
<body>
    <h1>Hello, world!<small>副标题</small></h1>
    <h2>Hello, world!</h2>
    <h3>Hello, world!</h3>
    <h4>Hello, world!</h4>
    <h5>Hello, world!</h5>
    <h6>Hello, world!</h6>
    <span class="h1">标题</span>
    <span class="h2">标题</span>
  </body>
```

### 排版 - 文本

段落 p

对齐方式

文本标记（下划线，删除线等等）

### 排版 - 对齐

css样式

- .text-left
- .text-center
- .text-right

### 排版 - 大小写

css 样式

- .text-lowercase
- .text-uppercase
- .text-capitalize

### 表格

### 表单

## viewport

设置meta viewport，可以使页面适合手机端显示

因为手机端的屏幕比较小，电脑上一个像素在手机端可以对应几个

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

viewport的属性在content中定义，多个属性使用逗号分隔

属性说明：

- width height 设置高宽
- user-scalabel 允许放大缩小
- initial-scale 设置初始化大小 数值为倍数
- maximum-scale minimum-scale

## 栅格系统(grid system)

是一种grid布局，按照行和列来布局

所有的行.row都要在容器中(.container/.container-fluid), 所有的.col都要在行.row中，每一行最多12列，如果超出了12，多出来的会放在下一行

.col-{1}-{2}

{1} 表示屏幕尺寸

- xs -- Extra small devices
- sm -- Small devices Tablets (平板电脑)
- md -- Medium devices Desktops
- lg -- Large devices Desktops

{2} 表示一列横跨的列数，类似于colspan，用数字表示，范围[1,12]

示例：`col-xs-2`,`col-sm-1`

当一行出现高度不同的column时，如果页面宽度过小

## 网页开发中的单位

- px 相对于屏幕分辨率的单位

  px的大小无法跟随屏幕放大缩小，不适合响应式开发

- em

  1em = 16px（不一定）

  em 是相对于父元素的字体大小，

  弊端，em不稳定，大小不固定

- rem 和 em类似

  rem会继承根元素的字体大小（html）

## 字体图标

### 图标好处

- 体积小便于加载
- 无需重复设计
- 方便引用

css了解@font-face

## bootstrap组件(component)

### 怪异的属性

1. role

   给一些特别的浏览器工具进行识别，如盲人浏览器

2. aria-label

   读屏软件使用的属性，

   通常使用在输入框，当输入框获取到焦点，读屏软件就可以读取

3. tabIndex

   设置tab键移动顺序

4. data-*

   html5新增的自定义属性，不会再页面显示，用于自己编程数据交互使用

### 图标

glyphion，

```
<button class="btn btn-default">
        <span class="glyphicon glyphicon-ok"></span>
        这是按钮
    </button>
```

### 下拉菜单

1. `.dropdown` 控制组件为下拉菜单
2. `.dropdown-menu-right` 代替 `pull-right`右对齐
3. divider分割线

### 控件组

.input-group

### 导航

1. `.nav`无序列表
2. `.nav-tabs` 可切换的导航
3. `.nav-pills` 代表胶囊导航
4. `.nav-justified`使导航垂直

### 分页

1. `.pagination` 在父元素中表示分页
2.  .page

## BootStrap javascript

js中是bootstrap的插件，需要引入jquery 和bootstrap.js

需要注意版本匹配问题

## 模板

https://www.cnblogs.com/sanhao/p/9184323.html