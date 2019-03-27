
---
title: "vue"
date: 2019-02-20T16:47:54+08:00
---
# vue

## vuex

vuex就是app的数据源，一个store

- state, 状态，相当于vue的data，存放各种数据；
- getter，相当于计算属性，主要对state的数据做二次加工，依赖state，当state改变时，getter自动发生更改；
- mutation， 直接改变state的途径，通过`store.commit(xxx，payload)`, 不能有异步方法
- action， store的异步任务，异步任务 -> store.commit改变state

其实state是我们需要处理的数据源，getter是state的变种，依赖于state， 而mutation、action更改state的方法，mutation直接更改，action通过mutation间接更改；

### State
在vue中使用state： `this.$store.state.xxx`

使用`mapState()`展开到vue文件的计算属性中

### Getter
getter比state稍微复杂一点点，就是getter可以传参数。

```js
{
    getters: {
        getTodoById: (state) => (id) => {
            return state.todos.find(todo => todo.id === id)
        },
        todosCount: (state) => {
            return state.todos.length
        }
    }
}

//xx.vue
{
    computed: {
        todosCount() {
            return this.$store.getters.todosCount
        },
        getTodoById(id) {
            return this.$store.getters.getTodoById(id)
        }
    }
}
```

使用mapGetter分发
