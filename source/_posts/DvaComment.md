---
title: DvaComment
date: 2018-07-10 11:17:35
tags:
---

# DvaComment

## 数据类型

### 类型

- Number    数值    {Number} [loginName] 用户的登录帐号
- String    字符串  {String} [name] 用户的名称
- Object    对象    {Object} [{page:number,size:number}={page:0,size:10}] 分页信息
- Function  方法    {Function(id:Number):Object}
- Union     组合    {Number|String}
- Generics  泛型    {Promise<Object>}

### 修饰

#### 修饰类型

- Nullable      ?基本类型
- Not Nullable  !基本类型

#### 修饰名称

- Optional  [名称]
- Default   [名称=defaultValue]
- Spread    ...名称

## services

每个方法都要有注释

```js
/**
 * 获取所有待办事项
 * @param {String} [params.name] 待办事项的名称
 * @param {String} [params.comment] 待办事项的 描述/备注
 * @param {Number} [params.status] 待办事项的 状态 0 -> 待办, 1 -> 完成, 2 -> 取消
 */
export async function todoQueryAll(params){
  return request('/api/v1/todos',{
    method: 'GET',
    query: params,
  })
}
```

## model

```js
export default {
  namespace: 'todo',
  state : {
    todos: [],
    currentStatus: 0,
  },
  effects: {
    // 获取所有的待办事项
    *fetchAll({payload},{call,put}){
      const res = getResponse(yield call(todoQueryAll, payload));
      if(!isEmpty(res)){
        yield put({
          type: 'updateState',
          payload: {
            todos: res,
          },
        });
      }
    },
  },
  reducers: {
    updateState(state,{payload}){
      return Object.assign(
        {},
        state,
        payload,
      );
    },
  },
}
```

## route

```jsx
@connect(({todo,loading})=>({todo,loading}))
export default class Todo extends React.PureComponent{
  /**
   * 渲染待办事项页面
   */
  render(){
    const { todo: {todos = [],currentStatus} } = this.props;
    return (
      map(todos,(todo)=>{
        if(isNumber(currentStatus)){
          return todo.status === currentStatus ? <TodoComponent todo={todo} /> : false
        }else{
          return <TodoComponent todo={todo} />
        }
      });
    );
  }
}
```

## component

```jsx
export default class TodoComponent extends React.PureComponent{

  statusMap = {
    0: '待办',
    1: '已完成',
    2: '取消',
  };

  render(){
    const { todo: {name,comment,status} = {} } = this.props;
    const { statusMap } = this;
    return (
      <div>
        { name } &nbsp;&nbsp;-&nbsp;&nbsp;{comment}<br />
        { statusMap[status] || '未知状态' }  <br />
      </div>
    );
  }
}
```
