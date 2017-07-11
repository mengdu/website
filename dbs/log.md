# log.js

开发node.js的时候,习惯用console.log老打印一些信息，然而node端的console.log并没有浏览器里的功能那么强。

比如显示当前console.log信息所在的代码行，有时node开发打印很多个console.log信息是总是不知道是哪里调用的，然后只能手动去添加`console.log('1', info)`,`console.log('2', info)`...
所以，log.js就是为了解决这一问题而开发的；log.js是什么？

log.js 是 node.js 的一个调试工具。和 `console.log` 功能类似,不同的是，log.js支持显示文件路径信息，调用log的行号，还有支持主题样式`info`，`error`，`success`，`warn`。

有了这样一个工具，调试信息更加一目了然了。

具体怎么实现，请查看源码（链接在文章末尾）。

## api

+ log(string)
+ log.info(string)
+ log.success(string)
+ log.error(string)
+ log.warn(string)

# 用法

```js
const log = require('./log.js')

log('欢迎使用log.js。')

log.info('这是info提示信息')
log.success('这是success提示信息')
log.error('这是error提示信息')
log.warn('这是warn提示信息')

// 自定义log
log.addLog('test', 'cyan')

log.test('这是自定义的log')

log.addLog('debug', 'magenta')

log.debug('这是自定义的log')

```

可以运行 `demo.js` 查看效果

## 命令

```bat
node demo.js --dev
```

*参数:*

+ `--dev` 开发模式，开发模式会出现文件名和行号 
+ `--dev-show-path` 文件名显示绝对路径

注：显示文件名和行号会影响js性能，上线项目请自行删掉log，或者不加上面两个参数，会使用console.log。

## 效果图


![截图1][1]

## 自定义log

```
log.addLog('名字', '颜色')

log.名字(str)

```

支持颜色有：
```
    white
    grey
    black
    blue
    cyan
    green
    magenta
    red
    yellow
```

## 期望

其实还可以加多点功能，比如：

+ 做更多的样式配置（请看https://github.com/Marak/colors.js）
+ 增加log的打印时间

## 项目地址

[log.js项目地址][2]


  [1]: https://github.com/mengdu/log.js/raw/master/imgs/20170701212625.png
  [2]: https://github.com/mengdu/log.js