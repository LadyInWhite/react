
# webpack

webpack是基于node的一套开发环境

webpack是把各种类型的文件(.js .css .html .jade .ts .scss)转化为以（js）为主跟部分静态文件（.png，.txt .jpg）的
1.转化 (gulp) 2.模块化(requirejs)
webpack就是替代gulp和requirejs

全局安装webpack
```js
cnpm install webpack -g
```

还要在项目的目录下安装webpack
```js
cnpm i webpack --save-dev
```

要生成一份webpack->webpack.config.js    gulp->gulpfile.js

webpack.config.js配置文件
关键有一个entry,还有一个output,通过引入一份base.js文件然经过webpack处理，然后输出到output/bundle.js
```js
var path=require('path');
module.exports={
    mode: 'development',
    entry:"./input/base.js",
    output: {
        path: path.resolve(__dirname, 'output'),
        filename: 'bundle.js'
    },
    //module处理非JS文件的模块
    module: {
        rules: [{
            //正则匹配 匹配所有的html文件并交给html-loader处理   require->text模块
            test: /\.html$/,
            use: 'html-loader'
        },{
            //正则匹配 匹配所有的html文件并交给html-loader处理   require->text模块
            test: /\.css$/,
            use: 'css-loader'
        }]
    }
}
```

直接在webpack.config.js文件夹下运行webpack命令
```
webpack
```

当打包出bundle.js后，新建一个index.html并在里面引入bundle.js文件


后端模块化，使用nodejs的模块化，实现了前端的模块化

定义模块
```
//define
module.exports={
    xheader(Vue){
        Vue.component('xheader',{
            template:`<div><header>头部</header></div>`
        })
    }
}
```

引入模块(在base.js里引入)
```
var Vue=require('./vue.js');
require('./components/xheader/xheader.js').xheader(Vue);
new Vue({
    el:'#demo',
    template:`
        <div>
            <xheader />
        </div>
    `
})
```

安装专门处理非js类型文件的模块
```js
cnpm i html-loader css-loader --save-dev
```
引入
```js
require('./xxx.html')
```

xxx-loaders专门处理非JS类型的文件,在webpack.config.js下配置
```js
module: {
	rules: [{
		//正则匹配 匹配所有的html文件并交给html-loader处理   require->text模块
		test: /\.html$/,
		use: 'html-loader'
	}]
}
```