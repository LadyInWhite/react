
# webpack

webpack�ǻ���node��һ�׿�������

webpack�ǰѸ������͵��ļ�(.js .css .html .jade .ts .scss)ת��Ϊ�ԣ�js��Ϊ�������־�̬�ļ���.png��.txt .jpg����
1.ת�� (gulp) 2.ģ�黯(requirejs)
webpack�������gulp��requirejs

ȫ�ְ�װwebpack
```js
cnpm install webpack -g
```

��Ҫ����Ŀ��Ŀ¼�°�װwebpack
```js
cnpm i webpack --save-dev
```

Ҫ����һ��webpack->webpack.config.js    gulp->gulpfile.js

webpack.config.js�����ļ�
�ؼ���һ��entry,����һ��output,ͨ������һ��base.js�ļ�Ȼ����webpack����Ȼ�������output/bundle.js
```js
var path=require('path');
module.exports={
    mode: 'development',
    entry:"./input/base.js",
    output: {
        path: path.resolve(__dirname, 'output'),
        filename: 'bundle.js'
    },
    //module�����JS�ļ���ģ��
    module: {
        rules: [{
            //����ƥ�� ƥ�����е�html�ļ�������html-loader����   require->textģ��
            test: /\.html$/,
            use: 'html-loader'
        },{
            //����ƥ�� ƥ�����е�html�ļ�������html-loader����   require->textģ��
            test: /\.css$/,
            use: 'css-loader'
        }]
    }
}
```

ֱ����webpack.config.js�ļ���������webpack����
```
webpack
```

�������bundle.js���½�һ��index.html������������bundle.js�ļ�


���ģ�黯��ʹ��nodejs��ģ�黯��ʵ����ǰ�˵�ģ�黯

����ģ��
```
//define
module.exports={
    xheader(Vue){
        Vue.component('xheader',{
            template:`<div><header>ͷ��</header></div>`
        })
    }
}
```

����ģ��(��base.js������)
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

��װר�Ŵ����js�����ļ���ģ��
```js
cnpm i html-loader css-loader --save-dev
```
����
```js
require('./xxx.html')
```

xxx-loadersר�Ŵ����JS���͵��ļ�,��webpack.config.js������
```js
module: {
	rules: [{
		//����ƥ�� ƥ�����е�html�ļ�������html-loader����   require->textģ��
		test: /\.html$/,
		use: 'html-loader'
	}]
}
```