## import

所有实例1 main.js 程序入口 2 math.js 被引用模块

参考：https://segmentfault.com/a/1190000012210929

### 命名导出

#### 方式1

```js
//math.js
// Case 1: export后面跟变量输出声明语句
export var PI = 3.14;

// Case 2: export后面直接跟变量定义语句
export var add = function (x, y) { // 导出函数print
    return x + y;
}
```

```js
//main.js
import * as math from './math';
console.log(math.PI);
console.log(math.add(1,2));
```

#### 方式2

导出多个变量 简写形式

```js
//math.js
var PI = 3.14;
var add = function (x, y) { 
    return x + y;
}
export { PI, add }; // 简写格式，统一列出需要输出的变量
```

### 默认导出