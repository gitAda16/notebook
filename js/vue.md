挂载点 vue绑定的html

模板 是挂载点的内容

实例 就是 new Vue()



### 指令：

v-text v-html

```
<div id="root" v-text="msg"></div>
        <script>
            new Vue({
                el: "#root",
                data: {
                    msg: "hello world, Vue!"
                }
            });
        </script>
```

### 事件

方法在methods中，使用this可以直接访问到data中的参数，dom会自动更新

使用v-on:事件名称绑定事件，也可以简写为@事件名称

```
<div id="root" v-on:click="handleClick">{{msg}}</div>
        <script>
            new Vue({
                el: "#root",
                data: {
                    msg: "hello world, Vue!"
                },
                methods:{
                    handleClick:function(e){
                        this.msg = 'ok';
                    }
                }
            });
        </script>
```

### 属性绑定和双向数据绑定

属性绑定 v-bind:属性名称=“titleVal” titleVal是data中定义的变量

v-bind缩写 :属性名称

v-*** 模板指令后的是一个js表达式 

```
<div id="root" >
            <div v-bind:title="titleVal">hello vue</div>
        </div>
        <script>
            new Vue({
                el: "#root",
                data: {
                    titleVal: "ok"
                }
            });
        </script>
```

双向绑定 可以从数据修改显示内容，也可以显示内容修改数据

v-model 双向绑定指令

input的value改变，content也会改变

content改变，input的value也会改变

```
<div id="root" >
            <div :title="titleVal">hello vue</div>
            <input v-model="content" />
            <div @click="handleClick">{{content}}</div>
        </div>
        <script>
            new Vue({
                el: "#root",
                data: {
                    titleVal: "ok ye",
                    content:"this is content"
                },
                methods:{
                    handleClick:function(){
                        this.content="ok";
                    }
                }
            });
        </script>
```

### 计算属性和侦听器

在computed计算属性

只有属性变化才会调用方法计算，否则会从缓存读取



```
<div id="root" >
            <div id="root">
                姓：<input v-model="firstName" />
                名：<input v-model="lastName" />
                <div>全名：{{fullName}}</div>
            </div>
            
        </div>
        <script>
            new Vue({
                el: "#root",
                data: {
                    firstName: "ok ye",
                    lastName:"this is content"
                },
                computed: {
                    fullName: function(){
                        return this.firstName +' ' + this.lastName
                    }
                }
            });
        </script>
```

计算属性缓存的例子

如果将`shownowFun()`替换成`shownow` 再点击按钮，会有不同的效果

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="./vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        <p>{{shownowFun()}}</p>
        <p>{{now}}</p>
        <button @click="change">点我</button>
    </div>
</body>
<script>
    
    new Vue({
        el: '#root',
        data: {
            now: 1
        },
        computed: {
            shownow: function(){
                return new Date();
            }
        },
        methods: {
            change () {
                this.now++;
            },
            shownowFun : function(){
                return new Date();
            }
        }
    });
</script>
</html>
```



侦听器 侦听data中数据的变化

在watch中实现，还可以侦听computed中的变量

`_.debounce` 是一个通过 Lodash 限制操作频率的函数。 详细例子可以看vue官网中的教程 侦听

```
<div id="root" >
            <div id="root">
                姓：<input v-model="firstName" />
                名：<input v-model="lastName" />
                <div>全名：{{fullName}} {{count}}</div>
            </div>
            
        </div>
        <script>
            new Vue({
                el: "#root",
                data: {
                    firstName: "ok ye",
                    lastName:"this is content",
                    count:0
                },
                computed: {
                    fullName: function(){
                        return this.firstName +' ' + this.lastName
                    }
                },
                watch:{
                    firstName:function(){
                        this.count++;
                    },
                    lastName:function(){
                        this.count++;
                    }
                }
            });
        </script>
```

### v-if v-show v-for指令

`v-if `如果if中的变量是true 则显示，否则不显示

下面的v-if可以换成`v-show` 效果一样

两者区别 `v-if `当为false，html标签会被移除

`v-show`为false时，只是增加style `display:none`

```
<div id="root" >
            <div v-if="show">hello</div>
            <button @click="handleClick">toogle</button>
        </div>
        <script>
            new Vue({
                el: "#root",
                data:{
                    show:false
                },
                methods: {
                    handleClick:function(){
                        this.show = !this.show;
                    }
                }
            });
        </script>
```

v-for 循环 会随list变化 动态变化

加上一个:key指令 可以提高循环效率，但是key不能重复，list不能重复

如果key值重复，会抛出异常

```
<div id="root" >
            <ul>
                <li v-for="item of list" :key="item">{{item}}</li>
            </ul>
        </div>
        <script>
            new Vue({
                el: "#root",
                data:{
                    list:[1,2,3]
                }
            });
        </script>
```

:key重复的话，可以使用index，但是如果list变化频繁，index会有问题

```
<div id="root" >
            <ul>
                <li v-for="(item, index) of list" :key="index">{{item}}</li>
            </ul>
        </div>
        <script>
            new Vue({
                el: "#root",
                data:{
                    list:['a','a','c']
                }
            });
        </script>
```

### 组件

#### 全局组件

 Vue.component

```
<div id="root" >
            <input v-model="todo">
            <button @click="add">提交</button>
            <ul>
                <todo-item></todo-item>
            </ul>
        </div>
        <script>
            Vue.component('todo-item', {
                template: '<li>item</li>'
            });
            </script>
```

局部组件

在实例中用component定义的组件是局部组件

```
<div id="root" >
            <input v-model="todo">
            <button @click="add">提交</button>
            <ul>
                <todo-item></todo-item>
            </ul>
        </div>
        <script>
            // Vue.component('todo-item', {
            //     template: '<li>item</li>'
            // });
            var todoItem = {
                template: '<li>item</li>'
            }
            new Vue({
                el: "#root",
                components:{
                    'todo-item':todoItem
                },
                data:{
                    todo:'',
                    list:[]
                },
                methods: {
                    add: function(){
                        this.list.push(this.todo);
                        this.todo = "";
                    }
                }
            });
        </script>
```

循环使用组件

```
<div id="root" >
            <input v-model="todo">
            <button @click="add">提交</button>
            <ul>
                <todo-item v-for="(item, index) of list" :key="index"
                :content="item"></todo-item>
            </ul>
        </div>
        <script>
            Vue.component('todo-item', {
                props: ['content'],//外部传递参数名
                template: '<li>{{content}}</li>'
            });
            var todoItem = {
                template: '<li>item</li>'
            }
            new Vue({
                el: "#root",
                // components:{
                //     'todo-item':todoItem
                // },
                data:{
                    todo:'',
                    list:[]
                },
                methods: {
                    add: function(){
                        this.list.push(this.todo);
                        this.todo = "";
                    }
                }
            });
        </script>
```

### 组件和实例

组件也是实例

实例是对指定标签映射的对象

组件中也可以实现实例中的功能

```
<div id="root" >
            <input v-model="todo">
            <button @click="add">提交</button>
            <ul>
                <todo-item v-for="(item, index) of list" :key="index"
                :content="item"></todo-item>
            </ul>
        </div>
        <script>
            Vue.component('todo-item', {
                props: ['content'],//外部传递参数名
                template: '<li @click="handle">{{content}}</li>',
                methods: {
                    handle: function(){
                        alert('hello '+this.content);
                    }
                }
            });
            var todoItem = {
                template: '<li>item</li>'
            }
            new Vue({
                el: "#root",
                data:{
                    todo:'',
                    list:[]
                },
                methods: {
                    add: function(){
                        this.list.push(this.todo);
                        this.todo = "";
                    }
                }
            });
        </script>
```

子组件和父组件之间通讯

$emit触发事件

```
<div id="root" >
            <input v-model="todo">
            <button @click="add">提交</button>
            <ul>
                <todo-item v-for="(item, index) of list" :key="index"
                :content="item"
                :index="index"
                @delete="handleDelete"></todo-item>
            </ul>
        </div>
        <script>
            //子组件
            Vue.component('todo-item', {
                props: ['content','index'],//外部传递参数名
                template: '<li @click="handle">{{content}} {{index}}</li>',
                methods: {
                    handle: function(){
                        this.$emit('delete',this.index);

                    }
                }
            });
            var todoItem = {
                template: '<li>item</li>'
            }
            //父组件
            new Vue({
                el: "#root",
                data:{
                    todo:'',
                    list:['a','b']
                },
                methods: {
                    add: function(){
                        this.list.push(this.todo);
                        this.todo = "";
                    },
                    handleDelete: function(index){
                        //alert(index);
                        this.list.splice(index,1);
                    }
                }
            });
        </script>
```

被实例过的标签中的元素还能被实例，这样嵌套的优先级，还有el选择器的优先级

vue如何调试

### vue cli

`npm install --global vue-cli`

初始化项目：`vue init webpack todolist`

以上命令不要使用gitbash运行

#### .vue文件

单文件组件

包含了 template，script，style

vue cli是一个构建工具 可以让程序员使用es6语法 main.js是程序的入口

vue中的template里面只能有一个根元素

### 样式

子组件父组件样式作用域，在style中加上scoped 使得样式只对自己有效，否则该样式为全局样式

```
<style scoped>
.item{
  color: yellowgreen
}
```

组件：

Quasar

elementui

实例：https://github.com/Neveryu/vue-cms