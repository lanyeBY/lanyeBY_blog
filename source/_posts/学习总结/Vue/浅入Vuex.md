---
title: 浅入Vuex
date: 2020-09-23 22:01
tags: Vue
catetory: 学习总结
---

### Vuex是什么
Vuex是一个专为Vue.js应用程序开发的状态管理模式。它采用集中式存储管理应用的所有组件的状态，并以响应的规则保证状态以一种可预测的方式发生变化。<br/>
状态资管理应用包含以下几个部分：
- `state`，驱动应用的数据源；
- `view`，以声明方式将`state`映射到视图；
- `actions`，响应在`view`上的用户输入导致的状态变化。

---

每一个`Vuex`应用的核心就是`store`。`store`不能直接被改变。改变`store`中的状态的唯一途径就是显式的提交`mutation`。

#### State

##### `mapState`辅助函数
当一个组件需要获取多个状态时，可以使用`mapState`辅助函数生成计算属性。

```javascript
import { mapState } from 'vuex';

export default {
  // ...
  computed: mapState({
    count: state => state.count,
    
    // 传字符串参数'count' 等同于 'state => state.count'
    countAlias: 'count',
    
    // 为了能够使用'this'获取局部状态，必须使用常规函数
    countPlusLocalState(state) {
      return state.count + this.localCount
    }
  })
}
```

当映射的计算属性名称与`state`的子节点名称相同时，我们也可以给`mapState`传一个字符串数组：

```javascript
computed: mapState([
  // 映射this.count为store.state.count
  'count'
])
```

当我们需要将`mapState`与其他局部计算属性混合使用的时候，可以借助`对象展开运算符`：

```javascript
computed: {
  locaComputed() { ... },
  ...mapState({
      // ...
  })
}
```

#### Getter

当我们需要把一些经过处理的`state`派生出去用作共享的时候，可以定义`getter`。就像计算属性一样，`getter`的返回值会根据它的依赖被缓存起来，且只有当它的依赖值发生了改变才会被重新计算。<br>
`Getter`接受`state`作为其第一个参数：

```javascript
state: {
  todos: [
    { id: 1, text: '...', done: true },
    { id: 2, text: '...', done: false },
  ]
},
getter: {
  doneTodos: state => {
    return state.todos.filter(todo => todo.done)
  }
}
```

##### 通过属性访问
`Getter`会暴露为`store.getter`对象，你可以以属性的形式访问这些值：

```javascript
store.getters.doneTodos // -> [{ id: 2, text: '...', done: false }]
```

`Getter`也可以接受其他`getter`作为第二个参数：

```javascript
getters: {
  // ...
  doneTodosCount: (state, getters) => {
    return getters.doneTodos.lenth
  }
}

// ...

store.getters.doneTodosCount // -> 1
```

##### `mapGetter`辅助函数

类似于`mapState`

#### Mutation
更改`Vuex`的`store`中的状态的唯一方法是提交`mutation`。`Vuex`中的`mutation`非常类似于事件：每个`mutation`都有一个字符串的 事件类型 (`type`) 和 一个 回调函数 (`handler`)：

```javascript
const store = new Vuex.Store({
  state: {
    count: 1
  },
  mutations: {
    increment (state) {
      // 变更状态
      state.count++
    }
  }
})
```

不能直接调用一个`mutation handler`。要唤醒一个`mutation handler`，你需要以相应的`type`调用`store.commit`方法：

```javascript
store.commit('increment')
```

##### 提交载荷(`Payload`)
可以向`store.commit`传入额外的参数，即`mutation`的 载荷（`payload`），一般为对象，这样可以包含多个字段：

```javascript
// ...
mutations: {
  increment (state, payload) {
    state.count += payload.amount
  }
}
```

也可以使用对象风格的提交方式:

```javascript
store.commit({
  type: 'increment',
  amount: 10
})
```

当使用对象风格的提交方式，整个对象都作为载荷传给`mutation`函数，因此`handler`保持不变：

```javascript
mutations: {
  increment (state, payload) {
    state.count += payload.amount
  }
}
```

##### `Mutation`必须是同步函数
任何在回调函数中进行的状态的改变都是不可追踪的。

##### mapMutation
使用`mapMutations`辅助函数将组件中的`methods`映射为`store.commit`调用:

```javascript
import { mapMutations } from 'vuex'

export default {
  // ...
  methods: {
    ...mapMutations([
      'increment', // 将 `this.increment()` 映射为 `this.$store.commit('increment')`

      // `mapMutations` 也支持载荷：
      'incrementBy' // 将 `this.incrementBy(amount)` 映射为 `this.$store.commit('incrementBy', amount)`
    ]),
    ...mapMutations({
      add: 'increment' // 将 `this.add()` 映射为 `this.$store.commit('increment')`
    })
  }
}
```

#### Action

`Action`类似于`mutation`，不同在于：
- `Action`提交的是`mutation`，而不是直接变更状态。
- `Action`可以包含任意异步操作。

```javascript
const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment (state) {
      state.count++
    }
  },
  actions: {
    increment (context) {
      context.commit('increment')
    }
  }
})
```

`Action`函数接受一个与`store`实例具有相同方法和属性的`context `对象，因此你可以调用`context.commit`提交一个`mutation`，或者通过`context.state`和`context.getters`来获取`state`和`getters`。

##### 分发`Action`
`Action`通过`store.dispatch`方法触发：

```javascript
store.dispatch('increment')

// 以载荷形式分发
store.dispatch('increment', {
  amount: 10
})

// 以对象形式分发
store.dispatch({
  type: 'incrementAsync',
  amount: 10
})
```

##### mapActions

使用`mapActions`辅助函数将组件的`methods`映射为`store.dispatch`调用：

```javascript
import { mapActions } from 'vuex'

export default {
  // ...
  methods: {
    ...mapActions([
      'increment', // 将 `this.increment()` 映射为 `this.$store.dispatch('increment')`

      // `mapActions` 也支持载荷：
      'incrementBy' // 将 `this.incrementBy(amount)` 映射为 `this.$store.dispatch('incrementBy', amount)`
    ]),
    ...mapActions({
      add: 'increment' // 将 `this.add()` 映射为 `this.$store.dispatch('increment')`
    })
  }
}
```
