## webpack是什么

webpack 是一个js打包工具，可以使js模块化开发

webpack 和 nodejs npm的关系

nodejs是一个后台运行js的运行环境

npm是nodejs的包管理工具，安装nodejs的时候会同时安装上npm

webpack是npm中的一个包，可以使用npm install webpack 安装

## webpack的基本使用方式

module.exports 对外提供模块

require 引用模块

## webpack命令

webpack sourceFile -o destFile

## package.json

此文件是nodejs的依赖包的索引，用npm install 可以安装所有罗列的插件

使用npm init 初始化出来package.json

## webpack.config.js

由于命令方式打包不太方便，一般使用配置文件的方式打包，配置文件即webpack.config.js

配置好配置文件后，只需运行命令webpack 即可

还可以在package.json中配置,如下所示，然后在命令行运行npm start

```
{
  "name": "learnnodejs",
  "version": "1.0.0",
  "description": "",
  "main": "hello.js",
  "dependencies": {},
  "devDependencies": {},
  "scripts": {
    "start": "webpack"//此处配置，json不支持注释，此处只做演示
  },
  "author": "",
  "license": "ISC"
}
```



## webpack构建本地服务器

如果希望浏览器监听代码修改，并自动刷新显示修改后的结果，可使用本地开发服务器，这个本地服务器是基于node.js构建的

首先要安装它为项目依赖

```
npm install --save-dev webpack-dev-server
```

然后在webpack.config.js中配置devserver

| devserver的配置选项 | 功能描述                                                     |
| ------------------- | ------------------------------------------------------------ |
| contentBase         | 默认webpack-dev-server会为根文件夹提供本地服务器，如果想为另外一个目录下的文件提供本地服务器，应该在这里设置其所在目录（本例设置到“public"目录） |
| port                | 设置默认监听端口，如果省略，默认为”8080“                     |
| inline              | 设置为`true`，当源文件改变时会自动刷新页面                   |
| historyApiFallback  | 在开发单页应用时非常有用，它依赖于HTML5 history API，如果设置为`true`，所有的跳转将指向index.html |

```
module.exports = {
  devtool: 'eval-source-map',

  entry:  __dirname + "/app/main.js",
  output: {
    path: __dirname + "/public",
    filename: "bundle.js"
  },

  devServer: {
    contentBase: "./public",//本地服务器所加载的页面所在的目录
    historyApiFallback: true,//不跳转
    inline: true//实时刷新
  } 
}
```

在`package.json`中的`scripts`对象中添加如下命令，用以开启本地服务器：

```
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "webpack",
    "server": "webpack-dev-server --open"
  },
```

在终端中输入`npm run server`即可在本地的`8080`端口查看结果

## Loader

Loader就是通过配置，去处理配置匹配的文件，进行相应处理

Loaders需要单独安装并且需要在`webpack.config.js`中的`modules`关键字下进行配置，Loaders的配置包括以下几方面：

- `test`：一个用以匹配loaders所处理文件的拓展名的正则表达式（必须）
- `loader`：loader的名称（必须）
- `include/exclude`:手动添加必须处理的文件（文件夹）或屏蔽不需要处理的文件（文件夹）（可选）；
- `query`：为loaders提供额外的设置选项（可选）

## Plugins

plugins和loader的区别，loader是在webpack打包构建的时候处理指定的源文件，plugin不是对单个文件，是对整个构建起作用

## webpack-dev-server