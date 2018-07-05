#react-redux的index.js的配置

1.引入模块
```js
cnpm i react-redux --save
cnpm i redux --save
```


2.在src->index.js下引用模块
//redux Provider是把store用在所有组件中
```js
import { Provider } from 'react-redux';
```
//createStore是创建仓库的方法
```js
import { createStore } from 'redux';
```

3.创建store仓库
```js
const store=createStore();
```

4.配置Reduce（不要修改state，而是返回一个新的state）
```js
function counter(state = {
  count: 0
}, action){
  const count = state.count
  switch (action.type) {
    case 'increase':
      return {
        ...state,
        count: count + 2
      }
    case 'multi':
      return Object.assign({}, state, {name: action.name});
    default:
      return state
  }
}
```

5.将配置的Reduce放入store中(第三步与第四步合并)
```js
const store=createStore((state = {
  count: 0
}, action) =>{
  const count = state.count
  switch (action.type) {
    case 'increase':
      return {
        ...state,
        count: count + 2
      }
    case 'multi':
      return Object.assign({}, state, {name: action.name});
    default:
      return state
  }
})
```
6.将<Provider store={store}></Provider>引用，
provider是一个组件，是的里面包含的组件都能拿到store里面的东西
```js
ReactDOM.render(
    <Provider store={store}>
        <div>
            <Xheader />
            <Xsearch />
            <Xmain />
            <Xpannel />
            <Xlifecycle />
            <Xfooter />
        </div>
    </Provider>
    , document.getElementById('root'));
registerServiceWorker();
```

#组件的使用
1.在组件中引入
```js
import { connect } from 'react-redux'
```
2.在原本的export default <组件 />写成以下形式
```js
export default connect((state) => {
    //他把store的state全部放到该组件的props里面
    return state
}, (dispatch) => {
    return {
        onIncreaseClick:(num,e) => {
            //可以触发多个
            dispatch({
            type:'showGallery',//触发的事件
            xxx:true,//改变的值
            })
        }
    }
})(组件)
```




