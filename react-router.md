1.安装模块
```js
npm i  react-router-dom --save-dev
```

2.在index.js里引入模块
```js
import { BrowserRouter as Router, Route, Link } from 'react-router-dom'
```

4.在index.js引入组件
```js
import Home from './components/page/home';
import Setting from './components/page/setting';
```

3.将<Router></Router>组件放入ReactDOM.render里,让router组件包含所有的组件，再配置路由
```js
ReactDOM.render(
    <Router>
        <Provider store={store}>
            <div>
                <Route exact path="/" component={Home}/>//路由为/的一定要在path前面加exact,要是不加，在跳转到其它路由时，其他页面的内容会加载在路由为/的页面下
                <Route path="/setting" component={Setting}/>
            </div>
        </Provider>
    </Router>
    , document.getElementById('root'));
registerServiceWorker();
```


 