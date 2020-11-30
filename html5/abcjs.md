<https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/001434501245426ad4b91f2b880464ba876a8e3043fc8ef000>

# 关键词



## node.js

在安装 Webpack 前，你本地环境需要支持 [node.js](http://www.runoob.com/nodejs/nodejs-install-setup.html)。

那我就开始学node.js

## npm

安装好node.js后，先认识一下npm 包管理器

## vs code

使用Visual Studio Code作为开发工具  简称 vs code

vs code使用文件夹作为工程目录，所有的js文件都存放在该目录下，此外 在工程目录下还需要一个.vscode的配置目录，存放vs code 需要的配置文件

## 模块

为了编写可维护的代码，我们把很多函数分组，分别放到不同的文件里，这样，每个文件包含的代码就相对较少，很多编程语言都采用这种组织代码的方式。在Node环境中，一个.js文件就称之为一个模块（module）。

使用模块有什么好处？

最大的好处是大大提高了代码的可维护性。其次，编写代码不必从零开始。当一个模块编写完毕，就可以被其他地方引用。我们在编写程序的时候，也经常引用其他模块，包括Node内置的模块和来自第三方的模块。

使用模块还可以避免函数名和变量名冲突。相同名字的函数和变量完全可以分别存在不同的模块中，因此，我们自己在编写模块时，不必考虑名字会与其他模块冲突。

在模块中对外输出变量

```
module.exports = variable;
```

输出的变量可以是任意类型

要引入其他模块输出的对象，用

```
var foo = require('other_module');
```

*问题，是否可以输出多个不同的变量？* 可以

### node.js基本模块

#### global

node.js 中的唯一的全局对象 global 

*如果想使用window对象，怎么使用*

有很多JavaScript代码既能在浏览器中执行，也能在Node环境执行，但有些时候，程序本身需要判断自己到底是在什么环境下执行的，常用的方式就是根据浏览器和Node环境提供的全局变量名称来判断

```
if (typeof(window) === 'undefined') {
    console.log('node.js');
} else {
    console.log('browser');
}
```

#### process

代表当前node.js进程

## webpack

### 安装

`-g`表示全局安装

npm install webpack -g

npm install webpack-cli -g

出现报错Error: Cannot find module 'webpack'

在本地开发npm模块的时候，我们可以使用npm link命令，将npm 模块链接到对应的运行项目中去，方便地对模块进行调试和测试

npm link webpack

### 命令行打包

```
# {extry file}出填写入口文件的路径，本文中就是上述main.js的路径，
# {destination for bundled file}处填写打包文件的存放路径
# 填写路径的时候不用添加{}
# -o -output 表示输出文件，必须要有这个参数，否则会报错
webpack {entry file} -0 {destination for bundled file}
```

### 配置文件打包

以上通过命令行模式不太方便，更好的办法是定义一个配置文件，在项目根目录新建webpack.config.js

```
module.exports = {
  entry:  __dirname + "/app/main.js",//已多次提及的唯一入口文件
  output: {
    path: __dirname + "/public",//打包后的文件存放的地方
    filename: "bundle.js"//打包后输出文件的文件名
  }
}
```

dirname是node.js的一个全局变量，指向项目的所在路径，但是我在node的命令行中找不到这个变量

有了这个配置之后，再打包文件，只需在终端里运行`webpack(非全局安装需使用node_modules/.bin/webpack)`命令就可以了，这条命令会自动引用`webpack.config.js`文件中的配置选项

### 更快捷的执行打包任务

在`package.json`中对`scripts`对象进行相关设置后，使用npm start命令即可打包

```
{
  "name": "webpack-sample-project",
  "version": "1.0.0",
  "description": "Sample webpack project",
  "scripts": {
    "start": "webpack" // 修改的是这里，JSON文件不支持注释，引用时请清除
  },
  "author": "zhang",
  "license": "ISC",
  "devDependencies": {
    "webpack": "3.10.0"
  }
}
```

### 如何调试

我要先成功打包，然后就可以了解如何调试代码

npm run build 即可开始打包

可以搜索webpack如何调试

在package.config.js中，设置devtool: 'eval-source-map'，devtool其他的值可以查询资料

然后在chrome中按F12 就可以开始调试，ctrl+p可以定位到文件中打断点，也可以在源码中写入debugger，那么运行时会自动在debugger位置打上断点



```
{
​        entry: `./static-wrappers/${env.type}.js`,
​        devtool: 'eval-source-map',
​        output: {
​            filename: outputFilename,
​            path: path.join(__dirname, "bin")
​        },
​        module: {
​            rules: [
​                {
​                    test: /\.js$/,
​                    exclude: /node_modules/,
​                    use: "babel-loader"
​                }
​            ]
​        },
​        plugins: [
​            new UglifyJsWebpackPlugin({
​                extractComments: {
​                    condition: /\!$/,
​                    banner: banner
​                }
​            })
​        ]
​    };
```

midi file 缺失

midi 可以看看 <https://github.com/paulrosen/MIDI.js>

## svg

## 名词

pitch ： 音高，可以计算出音符在五线谱中的哪个间隔中

音符使用音符类型+音高描述，音符名就是4分音符，8分音符等等

paper：指div，绘制的div

render：渲染页面，paper为render的一个属性

staffGroup : 是音符组？代表什么？是将音符每一个元素描述出来，一个音符由多个元素组成，如符头，符竿，符值等等，同时计算出音符的宽度

voices 在staffgroup中，voice的child描述了一个一个的音符,voices应该是指声道, voice是多个VoiceElement的数组，voiceElement.beams 为横线符值

meter 3/4 1/4

stem 符杆

beam 符尾

slurs 连唱线

triplets 三连音

## 问题记录

### 1 音符横向的位置如何计算

首先 横向的位置记录在AbsoluteElement.x中它位于staffGroup.voice.children中

x的位置计算算法位于abc_engraver_controller.engraveTune.setXSpacing中

先要计算出每个音符的宽度

计算下一个x的时候，间隔和音符长度有关系`this.nextx= x + (spacing*Math.sqrt(this.spacingduration*8));`

x=x+extrawidth 

### 2 符干的长度如何计算

在AbstractEngraver.prototype.addNoteToAbcElement中，竖线的长度为7pitch

### 3 绘制过程

先通过parser 将字符串解析成有结构的音符数据，包含音符类型，长度，音高，音符x方向位置

### 4 分析一下tune对象

tune代表一首乐谱，由lines组成，代表每一行乐谱

lines 为数组，由对象{staff, staffgroup}组成，staff和staffGroup分别是什么？

staffGroup是在abc_abstract_engraver.createABCLine创建的

staffGroup={

staff,

voices:[voiceElement:{child:[absoluteElement:child]}]

}

Tune和Tunebook

Tune={

version,

media,

metaText,

formatting,

lines,-- lines.staff staffgroup

staffNum,

voiceNum,

lineNum

}

staff:{

}

### 5 运行过程

abc_tunebook_svg--->abc_tunebook(转换成TuneBook)--abc_parse

abc_parse 过程

parse 会生成一个Tune，Tune对象由abc_tune实现

一行一行解析乐谱，方法parseLine

parseLine过程

​	abc_parse_header.parse_header,处理头部信息，并且可以判断出事头部信息还是乐曲信息 输入一行乐谱，输出{str:一行乐谱，‘命令’} 命令：regular（乐曲），newline，words，symbols，recurse

tempo是什么 abc_parse_header 523行,当解析到K的时候，会resolveTempo

解析音乐 abc_parse.parseRegularMusicLine

abc_parse中有一些方法 letter_to,可以看看 

“和[在音乐里表示什么？

### 6 音符svg素材不知道如何定位

音符素材在abc_glyphs中，我知道这个是通过path来绘制的，但是第一个参数用于定位，要如何设置才能恰好位置？

### 7 符干向上还是向下

如果音符的pitch<6 则向上，否则向下

## 分析过程

| 时间      | 关键词       | 任务                                                         |
| --------- | ------------ | ------------------------------------------------------------ |
| 2019/5/18 |              | 已经知道了首先解析乐谱字符串成为对象，将乐谱拆分为头部信息和乐曲信息，每个音符为一个object对象，这些都组合在Tune对象中，然后在根据Tune.staff生成staffGroup对象，这个对象记录了每个音符的位置，音符的组成单元；；找到了横向位置的计算方法，abc_engraver_controller.engraveTune.setXSpacing,下次着重看 |
| 2019/5/19 |              | 看了setxSpacing， 大致意思是 根据音符的宽度，计算出x的位置，细节还需要再看；目前我使用abc_glyphs绘制了音符，但是无法很好的控制位置 |
| 2019/5/20 |              | 不同时长的音符的宽度如何计算出来，创建音符的方法在abc_abstract_engraver中，如createNode，createBarLine, 音符线方向（上/下）当pitch>=6 ?down:up,方法：abc_abstract_engraver.addNoteToAbcElement |
| 2019/5/21 |              | relativeElement.pitch2是stem的终点，它有pitch 起点 pitch2终点 |
| 2019/5/25 |              | 在创建staffgroup的时候计算出每个音符的宽度，明天看setXSpacing,看看nextx如何计算 extrawidth没理解 minwidth 是x+图形的w+minspace |
| 2019/5/26 |              | setXSpacing中计算nextx就是 `max(x + (spacing*Math.sqrt(this.spacingduration*8)) , minx)`<br>在所有的x都计算完成后，rest 音符有特殊处理，需要在两个音符正中间；<br>moveY这个方法没看懂，为什么有两个参数，<br>解答：参数1 step 参数2 pitch，即在y轴方向移动pitch*step的位置，可以理解为移动pitch单元的位置<br>需要搞清楚staff.top是什么，暂时推断top是以pitch为单位的数字，基本上每个absoluteElement的top都是是所有relativeElement的top的最大值，relativeElement的Top就是pitch;<br>已经知道了音符的横向位置如何计算，五线谱的五条线如何绘制，绘制音高的方法，<br>接下来了解**和声**的绘制方法，还有**装饰音**的绘制 |
| 2019/6/6  |              | 早上复习了一下，staff.top又忘记了，下次再看看，然后看组合音，getBeamGroup就是用来获取符尾相连的音符 |
| 2019/6/7  | 符尾相连     | AbstractEngraver.createABCLine 计算出符尾相连 存放在VoiceElement.beams<br>EngraverController.prototype.engraveTune 在符尾相连计算出来后，等到setXspacing后，开始计算符尾相连和其符干的位置<br>如果音符时长不同，则在BeamElem.layout中调用createAdditionalBeams，把其余的beam计算出来，如果后面的音符时长小于前面的，则继续相连，否则结束<br>符尾相连的符干 和符尾 是在计算出xspace后才计算的，首先计算出符尾的startx,y 和endx, y，然后再计算符干的x 和 y，符干的终点y 和浮头保持一致，如果两个音符时长不同，符尾的画法<br>符尾相连已经看明白了，接下来看加线，和声 |
| 2019/6/16 |              | 加线也是在staffGroup中计算出来的，属于voiceElement的child的一员<br>将类图画出来<br>一行的宽度是如何计算出来的 |
| 2019/6/18 |              | 类图已经画出来                                               |
| 2019/6/19 | beam的计算   | beam的位置 如果是向下，则是最低音符-stemheight  向上 最高音符+stemheight<br>beam的倾斜度 取+-(最低-最高)/2 幅度不超过音符个数/2<br>三连音和连音 |
| 2019/6/20 | 连音和三连音 | 处理三连音和连唱线，先在parse.letter_to_open_slurs_and_triplets处理，类似于beam，标记出开始和结束 startSlur endSlur pitch中的startSlurs endSlurs怎么变成了数组 在abc_abstract_engraver.addSlursAndTies中 |
| 2019/6/25 |              | abc_abstract_engraver.addSlursAndTies中slurid是什么，还有 parse怎么把slur变成数组的 |
| 2019/7/1  |              | abc_tune.cleanUp cleanUpSlursInLine 把slur变成数组，为什么要使用数组？ |
| 2019/7/2  |              | 连音线的画法在abc_render.drawArc 贝塞尔曲线                  |
| 2019/7/4  |              | abc_render.drawArc 我复写了一个，在myexample中               |
| 2019/7/5  |              | 三连音的写法(3abc                                            |
| 2019/7/9  |              | 三连音的画法 在otherchildren中<br>看到现在，基本上主要的画法已经了解，接下来我要看一下他的编辑器是如何实现的，因为他可以动态呈现，主要了解动态过程 |

## 五线谱基础知识参考

<https://wenku.baidu.com/view/ef5ae93443323968011c92b7.html>



## 音符类型

时长 *

符头 *

符干 *

符尾 *

符尾相连 *

浮点

和声

小节线 *

连音

装饰音 倚音

重复

音速

连音符

三连音

## 改编

不从头开始做，而是直接在这个程序上修改

改造方案

1 映射音符

2 自定义stave数量

3 beam水平