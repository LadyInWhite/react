1.��װģ��
```js
npm i  react-router-dom --save-dev
```

2.��index.js������ģ��
```js
import { BrowserRouter as Router, Route, Link } from 'react-router-dom'
```

4.��index.js�������
```js
import Home from './components/page/home';
import Setting from './components/page/setting';
```

3.��<Router></Router>�������ReactDOM.render��,��router����������е������������·��
```js
ReactDOM.render(
    <Router>
        <Provider store={store}>
            <div>
                <Route exact path="/" component={Home}/>//·��Ϊ/��һ��Ҫ��pathǰ���exact,Ҫ�ǲ��ӣ�����ת������·��ʱ������ҳ������ݻ������·��Ϊ/��ҳ����
                <Route path="/setting" component={Setting}/>
            </div>
        </Provider>
    </Router>
    , document.getElementById('root'));
registerServiceWorker();
```


 