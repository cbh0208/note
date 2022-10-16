# vue


## 指令

### v-text

更新元素的 **textContent**

```html
<span v-text="msg"></span>
<!-- 等价于 -->
<span>{{msg}}</span>
<!-- 如果要更新部分的 textContent，需要使用 Mustache 插值({{msg}})  -->
<!--m:{{msg}} -->
```



###  v-html

更新元素的 **innerHTML**

```html
<div v-html="html"></div>
```



### v-show

- 根据表**达式的真假值**，切换元素的 `display` CSS property(元素保留)。

- 当条件变化时该指令触发**过渡效果**。

- 一般来说，`v-if` 有更高的切换开销，而 `v-show` 有更高的初始渲染开销。因此，如果需要非常频繁地切换，则使用 `v-show` 较好；如果在运行时条件很少改变，则使用 `v-if` 较好。




### v-if

- 根据**表达式的真假值**来有条件地渲染元素。

- 在切换时元素及它的数据绑定 / 组件被销毁并重建。如果元素是 `<template>`，将**提取**它的内容作为条件块。

- 当条件变化时该指令触发**过渡效果**。

- 当和 `v-for` 一起使用时，`v-if` 的优先级比 `v-for` 更高。




### v-else

前一兄弟元素必须有 `v-if` 或 `v-else-if`。

为 `v-if` 或者 `v-else-if` 添加“else 块”。

```html
<div v-if="Math.random() > 0.5">
  Now you see me
</div>
<div v-else>
  Now you don't
</div>
```



### v-else-if

前一兄弟元素必须有 `v-if` 或 `v-else-if`。

表示 `v-if` 的“else if 块”。可以链式调用。

```html
<div v-if="type === 'A'">
  A
</div>
<div v-else-if="type === 'B'">
  B
</div>
<div v-else-if="type === 'C'">
  C
</div>
<div v-else>
  Not A/B/C
</div>
```



### v-for

基于源数据多次渲染元素或模板块。此指令之值，必须使用特定语法 `alias in expression`，为当前遍历的元素提供别名

```html
<div v-for="item in items">
  {{ item.text }}
</div>
```

```html
<!-- 另外也可以为数组索引指定别名 (或者用于对象的键)-->
<div v-for="(item, index) in items"></div>
<div v-for="(value, name) in object"></div>
<div v-for="(value, name, index) in object"></div>
```



### v-on

**缩写**：`@`

绑定**事件监听器**。事件类型由参数指定。表达式可以是一个方法的名字或一个内联语句，如果没有修饰符也可以省略。

**修饰符**：

- `.stop` - 调用 `event.stopPropagation()`。
- `.prevent` - 调用 `event.preventDefault()`。
- `.capture` - 添加事件侦听器时使用 capture 模式。
- `.self` - 只当事件是从侦听器绑定的元素本身触发时才触发回调。
- `.{keyAlias}` - 仅当事件是从特定键触发时才触发回调。
- `.once` - 只触发一次回调。
- `.left` - 只当点击鼠标左键时触发。
- `.right` - 只当点击鼠标右键时触发。
- `.middle` - 只当点击鼠标中键时触发。
- `.passive` - `{ passive: true }` 模式添加侦听器

```html
<!-- 方法处理器 -->
<button v-on:click="doThis"></button>

<!-- 动态事件 -->
<button v-on:[event]="doThis"></button>

<!-- 内联语句 -->
<button v-on:click="doThat('hello', $event)"></button>

<!-- 缩写 -->
<button @click="doThis"></button>

<!-- 动态事件缩写 -->
<button @[event]="doThis"></button>

<!-- 停止冒泡 -->
<button @click.stop="doThis"></button>

<!-- 阻止默认行为 -->
<button @click.prevent="doThis"></button>

<!-- 阻止默认行为，没有表达式 -->
<form @submit.prevent></form>

<!-- 串联修饰符 -->
<button @click.stop.prevent="doThis"></button>

<!-- 键修饰符，键别名 -->
<input @keyup.enter="onEnter" />

<!-- 点击回调只会触发一次 -->
<button v-on:click.once="doThis"></button>

<!-- 对象语法 -->
<button v-on="{ mousedown: doThis, mouseup: doThat }"></button>
```

在子组件上监听自定义事件 (当子组件触发“my-event”时将调用事件处理器)：

```html
<my-component @my-event="handleThis"></my-component>

<!-- 内联语句 -->
<my-component @my-event="handleThis(123, $event)"></my-component>
```



### v-bind

**缩写**：`:`

**单向绑定**

动态地绑定一个或多个 attribute，或一个组件 prop 到表达式。

```vue
<!-- 绑定 attribute -->
<img v-bind:src="imageSrc" />

<!-- 动态 attribute 名 -->
<button v-bind:[key]="value"></button>

<!-- 缩写 -->
<img :src="imageSrc" />

<!-- 动态 attribute 名缩写 -->
<button :[key]="value"></button>

<!-- 内联字符串拼接 -->
<img :src="'/path/to/images/' + fileName" />

<!-- class 绑定 -->
<div :class="{ red: isRed }"></div>
<div :class="[classA, classB]"></div>
<div :class="[classA, { classB: isB, classC: isC }]">

  <!-- style 绑定 -->
  <div :style="{ fontSize: size + 'px' }"></div>
  <div :style="[styleObjectA, styleObjectB]"></div>

  <!-- 绑定一个全是 attribute 的对象 -->
  <div v-bind="{ id: someProp, 'other-attr': otherProp }"></div>

  <!-- prop 绑定。"prop" 必须在 my-component 声明 -->
  <my-component :prop="someThing"></my-component>

  <!-- 通过 $props 将父组件的 props 一起传给子组件 -->
  <child-component v-bind="$props"></child-component>

  <!-- XLink -->
  <svg><a :xlink:special="foo"></a></svg>  

```

`.camel` 修饰符允许在使用 DOM 模板时将 `v-bind` property 名称驼峰化，例如 SVG 的 `viewBox` property：

```html
<svg :view-box.camel="viewBox"></svg>
```

在使用字符串模板或通过 `vue-loader` / `vueify` 编译时，无需使用 `.camel`。



### v-model

实现**表单**输入和应用状态之间的**双向绑定**

不能直接绑定`props`

```html
<div id="two-way-binding">
  <p>{{ message }}</p>
  <input v-model="message" />
  <!-- //限制于：
	<input>
	<select>
	<textarea>
	components -->
  <!-- 修饰符
	.lazy - 监听 change 而不是 input 事件
    .number - 输入字符串转为有效的数字
    .trim - 输入首尾空格过滤 -->
</div>
```

```javascript
const TwoWayBinding = {
  data() {
    return {
      message: 'Hello Vue!'
    }
  }
}

Vue.createApp(TwoWayBinding).mount('#two-way-binding')
```



### v-slot

**缩写**：`#`

提供具名插槽或需要接收 prop 的插槽。

```html
<!-- 具名插槽 -->
<base-layout>
  <template v-slot:header>
    Header content
  </template>

  <template v-slot:default>
    Default slot content
  </template>

  <template v-slot:footer>
    Footer content
  </template>
</base-layout>

<!-- 接收 prop 的具名插槽 -->
<infinite-scroll>
  <template v-slot:item="slotProps">
    <div class="item">
      {{ slotProps.item.text }}
    </div>
  </template>
</infinite-scroll>

<!-- 接收 prop 的默认插槽，使用了解构 -->
<mouse-position v-slot="{ x, y }">
  Mouse position: {{ x }}, {{ y }}
</mouse-position>
```



### v-pre

跳过这个元素和它的子元素的编译过程。可以用来显示原始 Mustache 标签。跳过大量没有指令的节点会加快编译。

```html
<span v-pre>{{ this will not be compiled }}</span>
```



### v-cloak

这个指令保持在元素上直到关联组件实例结束编译。和 CSS 规则如 `[v-cloak] { display: none }` 一起用时，这个指令可以**隐藏未编译的 Mustache 标签**直到**组件实例准备完毕**。

```css
[v-cloak] {
  display: none;
}
```

```html
<div v-cloak>
  {{ message }}
</div>
```



### v-once

只渲染元素和组件**一次**。随后的重新渲染，元素/组件及其所有的子节点将被视为静态内容并跳过。这可以用于优化更新性能。

```html
<!-- 单个元素 -->
<span v-once>This will never change: {{msg}}</span>
<!-- 有子元素 -->
<div v-once>
  <h1>comment</h1>
  <p>{{msg}}</p>
</div>
<!-- 组件 -->
<my-component v-once :comment="msg"></my-component>
<!-- `v-for` 指令 -->
<ul>
  <li v-for="i in list" v-once>{{i}}</li>
</ul>
```



#### v-is







## 特殊指令

### key

`key` 特殊 attribute 主要用做 Vue 的虚拟 DOM 算法的提示，以在比对新旧节点组时辨识 VNodes。如果不使用 key，Vue 会使用一种算法来最小化元素的移动并且尽可能尝试就地修改/复用相同类型元素。而使用 key 时，它会基于 key 的顺序变化重新排列元素，并且 key 不再存在的元素将始终被移除/销毁。

有相同父元素的子元素必须有**唯一的 key**。重复的 key 会造成渲染错误。

### ref

`ref` 被用来给元素或子组件注册引用信息。引用信息将会被注册在父组件的 `$refs` 对象上。如果在普通的 DOM 元素上使用，引用指向的就是那个 **DOM 元素**；如果用在子组件上，引用就指向**组件实例**：

```vue
<!-- vm.$refs.p 会是 DOM 节点 -->
<p ref="p">hello</p>

<!-- vm.$refs.child 会是子组件实例 -->
<child-component ref="child"></child-component>

<!-- 当动态绑定时，我们可以将 ref 定义为回调函数，显式地传递元素或组件实例 -->
<child-component :ref="(el) => child = el"></child-component>
```



## 选项

### 数据

#### data

组件的 `data` 选项是一个函数。Vue 在创建新组件实例的过程中调用此函数。它应该返回一个对象，然后 Vue 会通过响应性系统将其包裹起来，并以 `$data` 的形式存储在组件实例中。为方便起见，该对象的任何顶级 property 也直接通过组件实例暴露出来：

```javascript
const app = Vue.createApp({
  data() {
    return { count: 4 }
  }
})

const vm = app.mount('#app')

console.log(vm.$data.count) // => 4
console.log(vm.count)       // => 4

// 修改 vm.count 的值也会更新 $data.count
vm.count = 5
console.log(vm.$data.count) // => 5

// 反之亦然
vm.$data.count = 6
console.log(vm.count) // => 6
```



####  props

用于**从父组件接收数据**的数组或对象

可以是基于数组的简单语法，也可以是基于对象的支持诸如类型检测、自定义验证和设置默认值等高阶配置的语法。

```javascript
const app = createApp({})

// 简单语法
app.component('props-demo-simple', {
  props: ['size', 'myMessage']
})

// 对象语法，提供验证
app.component('my-component', {
  props: {
    // 基础的类型检查 (`null` 和 `undefined` 会通过任何类型验证)
    propA: Number,
    // 多个可能的类型
    propB: [String, Number],
    // 必填的字符串
    propC: {
      type: String,
      required: true
    },
    // 带有默认值的数字
    propD: {
      type: Number,
      default: 100
    },
    // 带有默认值的对象
    propE: {
      type: Object,
      // 对象或数组默认值必须从一个工厂函数获取
      default() {
        return { message: 'hello' }
      }
    },
    // 自定义验证函数
    propF: {
      validator(value) {
        // 这个值必须匹配下列字符串中的一个
        return ['success', 'warning', 'danger'].includes(value)
      }
    },
    // 具有默认值的函数
    propG: {
      type: Function,
      // 与对象或数组默认值不同，这不是一个工厂函数 —— 这是一个用作默认值的函数
      default() {
        return 'Default function'
      }
    }
  }
})
```



#### methods

用 `methods` 选项向组件实例添加方法，它应该是一个包含所需方法的对象：

```js
const app = Vue.createApp({
  data() {
    return { count: 4 }
  },
  methods: {
    increment() {
      // `this` 指向该组件实例
      this.count++
    }
  }
})

const vm = app.mount('#app')

console.log(vm.count) // => 4

vm.increment()

console.log(vm.count) // => 5
```

Vue 自动为 `methods` 绑定 `this`，以便于它始终指向组件实例。这将确保方法在用作事件监听或回调时保持正确的 `this` 指向。在定义 `methods` 时应**避免使用箭头函数**，因为这会阻止 Vue 绑定恰当的 `this` 指向。

这些 `methods` 和组件实例的其它所有 property 一样可以在组件的模板中被访问。在模板中，它们通常被当做事件监听使用：

```html
<button @click="increment">Up vote</button>
```

在上面的例子中，点击 `<button>` 时，会调用 `increment` 方法。



#### computed

对于任何包含响应式数据的复杂逻辑，都应该使用**计算属性**。

实际上和data是一类

擅长处理的场景：**一个数据受多个数据影响**

```html
<div id="computed-basics">
  <p>Has published books:</p>
  <span>{{ publishedBooksMessage }}</span>
</div>
```

```js
Vue.createApp({
  data() {
    return {
      author: {
        name: 'John Doe',
        books: [
          'Vue 2 - Advanced Guide',
          'Vue 3 - Basic Guide',
          'Vue 4 - The Mystery'
        ]
      }
    }
  },
  computed: {
    // 计算属性的 getter
    publishedBooksMessage() {
      // `this` 指向 vm 实例
      return this.author.books.length > 0 ? 'Yes' : 'No'
    }
  }
}).mount('#computed-basics')
```

```javascript
    computed:{
        isAll:{
            get(){
                return this.total===this.doneTotal&&this.total>0
            },
            set(value){
                this.ckeckAllTodo(value)
            }
        }
    }
```



#### watch

一个对象，键是要侦听的响应式 property——包含了 data或 computed property，而值是**对应的回调函数**。值也可以是**方法名**，或者**包含额外选项的对象**。组件实例将会在实例化时调用 `$watch()`

擅长处理的场景：**一个数据受多个数据影响**

```javascript
const app = createApp({
  data() {
    return {
      a: 1,
      b: 2,
      c: {
        d: 4
      },
      e: 5,
      f: 6
    }
  },
  watch: {
    // 侦听顶级 property
    a(val, oldVal) {
      console.log(`new: ${val}, old: ${oldVal}`)
    },
    // 字符串方法名
    b: 'someMethod',
    // 该回调会在任何被侦听的对象的 property 改变时被调用，不论其被嵌套多深
    c: {
      handler(val, oldVal) {
        console.log('c changed')
      },
      deep: true
    },
    // 侦听单个嵌套 property
    'c.d': function (val, oldVal) {
      // do something
    },
    // 该回调将会在侦听开始之后被立即调用
    e: {
      handler(val, oldVal) {
        console.log('e changed')
      },
      immediate: true
    },
    // 你可以传入回调数组，它们会被逐一调用
    f: [
      'handle1',
      function handle2(val, oldVal) {
        console.log('handle2 triggered')
      },
      {
        handler: function handle3(val, oldVal) {
          console.log('handle3 triggered')
        }
        /* ... */
      }
    ]
  },
  methods: {
    someMethod() {
      console.log('b changed')
    },
    handle1() {
      console.log('handle 1 triggered')
    }
  }
})

const vm = app.mount('#app')

vm.a = 3 // => new: 3, old: 1
```

```

```



#### emit

从组件**触发自定义事件**

emits 可以是简单的数组，也可以是对象，后者允许配置事件验证。

```vue
<!-- 1.事件 --> 
demo(a){

}

<!-- 2.绑定到组件 -->
<Demo @d="demo"></Demo>

<!-- 3.组件使用 --> 
emits: ['demo'],
created() {
    this.$emit('demo',a)
  }
})


```



```javascript
const app = createApp({})

// 数组语法
app.component('todo-item', {
  emits: ['check'],
  created() {
    this.$emit('check')
  }
})

// 对象语法
app.component('reply-form', {
  emits: {
    // 没有验证函数
    click: null,

    // 带有验证函数
    submit: payload => {
      if (payload.email && payload.password) {
        return true
      } else {
        console.warn(`Invalid submit event payload!`)
        return false
      }
    }
  }
})


app.component('todo-item', {
  template: `
    <li>
      {{ title }}
      <button @click="$emit('remove')">Remove</button>
    </li>
  `,
  props: ['title'],
  emits: ['remove']
})
```



### DOM



#### template



####  render



### 生命周期钩子

#### beforeCreate

可以发请求，但是不能赋值给data里面的数据



#### created

发请求，初始渲染的工作在此处执行



#### beforeMount

虚拟DOM生成，数据未挂载



#### mounted

虚拟DOM解析，数据已经挂载，进行获取DOM元素



#### beforeUpdate

数据更新之前调用



#### update

数据更新之后调用



#### activated



#### deactivated



#### beforeUnmount

在销毁之前调用



#### unmounted

在销毁之后调用，定时器清除，事件移除都可以在此处去写



#### errorCaptured



#### renderTracked



#### renderTriggered



### 选项/资源

#### directives



#### components



### 组合

#### mixins



#### extends



#### provide / inject



#### setup



### 杂项

#### name



#### delimiters



#### inheritAttrs



## 实例 property



### $refs

```vue
// 一个对象，持有注册过 ref attribute 的所有 DOM 元素和组件实例

<!-- vm.$refs.p 会是 DOM 节点 -->
<p ref="p">hello</p>

<!-- vm.$refs.child 会是子组件实例 -->
<child-component ref="child"></child-component>

<!-- 当动态绑定时，我们可以将 ref 定义为回调函数，显式地传递元素或组件实例 -->
<child-component :ref="(el) => child = el"></child-component>
```

## 实例方法

### $emit

触发当前实例上的事件。附加参数都会传给监听器回调。

```

```



### $nextTick

将回调延迟到下次 DOM 更新循环之后执行。在修改数据之后立即使用它，然后等待 DOM 更新。它跟全局方法 `nextTick` 一样，不同的是回调的 `this` 自动绑定到调用它的实例上。

```

```









## 生命周期

![](https://v3.cn.vuejs.org/images/lifecycle.svg)

### errorCaptured

- 函数返回false可以阻止错误继续向上传递（但还是会传递给app.config.errorHandler）



### renderTracked

- 状态跟踪

- 状态跟踪在一开始渲染页面时就会触发，触发顺序：beforeMounted - renderTracked - mounted

- 页面更新也会触发，触发顺序：beforeUpdate - renderTracked - updated

  ```javascript
  //event对象
  {
   effect: {...},
   key: "girls",               //操作的键
   target: {girls:{...},...},  //操作的目标对象
   type: "get"                 //哪个操作跟踪了组件
  }
  ```

### renderTriggered

- 状态触发
- 操作页面的显示的数据（引起虚拟DOM重渲染）就会触发，触发顺序：renderTriggered - beforeUpdate



## 组件







```vue
<!--  -->
<template>
	<div></div>
</template>

<script>
export default {
    name:"demo",
    data() {
        return {

        }
    },
    //生命周期 - 创建完成（访问当前this实例）
    created() {

    },
    //生命周期 - 挂载完成（访问DOM元素）
    mounted() {

    }
}
</script>
<style scoped>
/* @import url(); 引入css类 */

</style>
```

```javascript
//导入
import demo from './components/demo.vue'
```



### 插槽

#### 插槽内容

```html
<!-- todo-button 组件模板 -->
<button class="btn-primary">
  <slot></slot>
</button>
```

```html
<todo-button>
  <!-- 添加一个Font Awesome 图标 -->
  <i class="fas fa-plus"></i>
  Add todo
</todo-button>
```

#### 具名插槽

```html
<div class="container">
  <header>
    <!-- 我们希望把页头放这里 -->
  </header>
  <main>
    <!-- 我们希望把主要内容放这里 -->
  </main>
  <footer>
    <!-- 我们希望把页脚放这里 -->
  </footer>
</div>
```

```html
<base-layout>
  <template v-slot:header>
    <h1>Here might be a page title</h1>
  </template>

  <template v-slot:default>
    <p>A paragraph for the main content.</p>
    <p>And another one.</p>
  </template>

  <template v-slot:footer>
    <p>Here's some contact info</p>
  </template>
</base-layout>
```



### 单文件组件

命名：要么始终是**单词大写开头**(PascalCase)，要么始终是**横线连接**(kebab-case)

```vue
<template>
	<div></div>
</template>

<script>
export default {
    name:"",
    data() {
        return {
        }
    },

</script>

<style scoped>
</style>
```



### 自定义事件

```vue
<!-- 1.事件 --> 
demo(a){

}

<!-- 2.绑定到组件 -->
<Demo @d="demo"></Demo>

<!-- 3.组件使用 --> 
emits: ['demo'],
created() {
    this.$emit('demo',a)
  }
})


```



## 内置组件

### keep-alive

- `<keep-alive>` 包裹动态组件时，会缓存不活动的组件实例，而不是销毁它们。和 `<transition>` 相似，`<keep-alive>` 是一个抽象组件：它自身不会渲染一个 DOM 元素，也不会出现在组件的父组件链中。
- 当组件在 `<keep-alive>` 内被切换时，它的 `mounted` 和 `unmounted` 生命周期钩子不会被调用，取而代之的是 `activated` 和 `deactivated`。(这会运用在 `<keep-alive>` 的直接子节点及其所有子孙节点。)
- 主要用于保留组件状态或避免重新渲染
- 注意，`<keep-alive>` 是用在其一个直属的子组件被切换的情形。如果你在其中有 `v-for` 则不会工作。如果有上述的多个条件性的子元素，`<keep-alive>` 要求同时只有一个子元素被渲染。
- 

```vue
<!-- 基本 -->
<keep-alive>
  <component :is="view"></component>
</keep-alive>

<!-- 多个条件判断的子组件 -->
<keep-alive>
  <comp-a v-if="a > 1"></comp-a>
  <comp-b v-else></comp-b>
</keep-alive>

<!-- 和 `<transition>` 一起使用 -->
<transition>
  <keep-alive>
    <component :is="view"></component>
  </keep-alive>
</transition>
```

- `<router-view>`

  ```vue
  <!-- <router-view> can no longer be used directly inside <transition> or <keep-alive>. -->
  <router-view v-slot="{ Component }">
    <keep-alive>
      <component :is="Component" />
    </keep-alive>
  </router-view>
  ```

- **`include` 和 `exclude`**

  `include` 和 `exclude` prop 允许组件有条件地缓存。二者都可以用逗号分隔字符串、正则表达式或一个数组来表示：

  ```vue
  <!-- 逗号分隔字符串 -->
  <keep-alive include="a,b">
    <component :is="view"></component>
  </keep-alive>
  
  <!-- regex (使用 `v-bind`) -->
  <keep-alive :include="/a|b/">
    <component :is="view"></component>
  </keep-alive>
  
  <!-- Array (使用 `v-bind`) -->
  <keep-alive :include="['a', 'b']">
    <component :is="view"></component>
  </keep-alive>
  ```

- **`max`**

  最多可以缓存多少组件实例。一旦这个数字达到了，在新实例被创建之前，已缓存组件中最久没有被访问的实例会被销毁掉。

  ```html
  <keep-alive :max="10">
    <component :is="view"></component>
  </keep-alive>
  ```

## 组合式API



### setup()

一个组件选项，在创建组件**之前**执行，一旦 `props` 被解析，并作为组合式 API 的入口点

执行 `setup` 时，组件实例尚未被创建。因此，你只能访问以下 property：

- `props`,`attrs`,`slots`,`emit`

换句话说，你**将无法访问**以下组件选项：

- `data`,`computed`,`methods`



两个**入参**:

- `props`

  接收props属性

  ```vue
  <template>
    <div></div>
  </template>
  <script>
    export default {
      props:{demo:{type:string}},
      setup(props) {
        console.log(props.demo)
        // 暴露给模板
        return {
        }
      }
    }
  </script>
  ```

- `context`

  `context` 是一个普通的 JavaScript 对象(可解构)，它暴露组件的三个 property：

  - context.attrs

    ```js
    context.attrs.r
    // r为父组件处理数据但未用props接收
    ```

  - context.slots

    ```js
    context.slots
    // 插槽内容
    
    context.slots.default()
    // 默认插槽内容
    ```

  - context.emit

    ```js
    context.emit('demo','鸢一折纸')
    // 触发自定义的demo事件,传递参数
    ```







```vue
<!-- MyBook.vue -->
<template>
  <div>{{ readersNumber }} {{ book.title }}</div>
</template>

<script>
  import { ref, reactive } from 'vue'

  export default {
    setup() {
      const readersNumber = ref(0)
      const book = reactive({ title: 'Vue 3 Guide' })

      // 暴露给模板
      return {
        readersNumber,
        book
      }
    }
  }
</script>
```





### 常用API

#### ref()

`ref()`函数用来创建响应式数据对象

`ref()`返回值为对象(只有一个`value`属性)

```vue
<template>
    <div>
        {{a}}<input type="text" v-model="a">
    </div>
</template>

<script>
import {ref} from 'vue'
export default {
    name:"Demo",
    setup(){
        const a=ref(0)
        return{
            a
        }
    }
}
</script>
```

#### reactive()

`reactive()`函数用来创建响应式对象

```vue
<template>
    <div>
        {{a.name}}---{{a.id}}
    </div>
</template>

<script>
import {reactive} from 'vue'
export default {
    name:"Demo",
    setup(){
        const a=reactive({name:'鸢一折纸',id:'angel'})
        return{
            a
        }
    }
}
</script>
```

#### toRefs()

`toRefs()`函数常用于解构响应式对象



#### computed()

`computed()` 用来创建计算属性,返回一个ref对象

```vue
<template>
    <div>
        {{b}}
    </div>
</template>

<script>
import {reactive,computed} from 'vue'
export default {
    name:"Demo",
    setup(){
        const a=reactive({name:'鸢一折纸',id:'angel'})
        const b=computed(()=>{
            return 'name='+a.name+'; id='+a.id
        })

        return{
            b
        }
    }
}
</script>

<style scoped>

</style>
```





#### watch()























### 生命周期钩子

- ~~`beforeCreate`~~ -> 使用 `setup()`
- ~~`created`~~ -> 使用 `setup()`
- `beforeMount` -> `onBeforeMount`
- `mounted` -> `onMounted`
- `beforeUpdate` -> `onBeforeUpdate`
- `updated` -> `onUpdated`
- `beforeUnmount` -> `onBeforeUnmount`
- `unmounted` -> `onUnmounted`



- `errorCaptured` -> `onErrorCaptured`
- `renderTracked` -> `onRenderTracked`
- `renderTriggered` -> `onRenderTriggered`
- `activated` -> `onActivated`
- `deactivated` -> `onDeactivated`



### Provide / Inject



### getCurrentInstance

`getCurrentInstance` 支持访问内部组件实例。

`getCurrentInstance` **只能**在 **setup**或**生命周期钩子**中调用。





# vue-cli

环境搭建

```shell
npm install -g @vue/cli
```

```
vue create my-vue
```













## vue.config.js

```javascript
// vue.config.js
// 手脚架配置
module.exports = {

}
```

### configureWebpack

#### 设置目录别名

```js
module.exports = {
    configureWebpack:{
        resolve:{
            alias:{
                'assets':'@/assets',
                'components':'@/components',
                'network':'@/network',
                'utils':'@/utils',
                'views':'@/views'
            }
        }
    },
    publicPath:'./'
}
```



### devServer.proxy



```JS
module.exports = {
  devServer: {
    proxy: 'http://localhost:4000'
  }
}
```

```JS
module.exports = {
  devServer: {
    proxy: {
      '/api': {
        target: '<url>',
        ws: true,
        changeOrigin: true
      },
      '/foo': {
        target: '<other_url>'
      }
    }
  }
}
```



### ----



# vue-router



```html
<script src="https://unpkg.com/vue@3"></script>
<script src="https://unpkg.com/vue-router@4"></script>

<div id="app">
  <h1>Hello App!</h1>
  <p>
    <!--使用 router-link 组件进行导航 -->
    <!--通过传递 `to` 来指定链接 -->
    <!--`<router-link>` 将呈现一个带有正确 `href` 属性的 `<a>` 标签-->
    <router-link to="/">Go to Home</router-link>
    <router-link to="/about">Go to About</router-link>
  </p>
  <!-- 路由出口 -->
  <!-- 路由匹配到的组件将渲染在这里 -->
  <router-view></router-view>
</div>
```

```javascript
// 1. 定义路由组件.
// 也可以从其他文件导入
const Home = { template: '<div>Home</div>' }
const About = { template: '<div>About</div>' }

// 2. 定义一些路由
// 每个路由都需要映射到一个组件。
// 我们后面再讨论嵌套路由。
const routes = [
  { path: '/home', component: Home },
  { path: '/about', component: About },
  { path: '/', redirect:'/home'}
]

// 3. 创建路由实例并传递 `routes` 配置
// 你可以在这里输入更多的配置，但我们在这里
// 暂时保持简单
const router = VueRouter.createRouter({
  // 4. 内部提供了 history 模式的实现。为了简单起见，我们在这里使用 hash 模式。
  history: VueRouter.createWebHashHistory(),
  routes, // `routes: routes` 的缩写
})

// 5. 创建并挂载根实例
const app = Vue.createApp({})
//确保 _use_ 路由实例使
//整个应用支持路由。
app.use(router)

app.mount('#app')
```

```javascript
// Home.vue
export default {
  computed: {
    username() {
      // 我们很快就会看到 `params` 是什么
      return this.$route.params.username
    },
  },
  methods: {
    goToDashboard() {
      if (isAuthenticated) {
        this.$router.push('/dashboard')
      } else {
        this.$router.push('/login')
      }
    },
  },
}
```



## 内置组件

#### router-link

- `<router-link>` 组件支持用户在具有路由功能的应用中 (点击) 导航。
-  通过 `to` 属性指定目标地址，默认渲染成带有正确链接的 `<a>` 标签，可以通过配置 `tag` 属性生成别的标签.。
- 另外，当目标路由成功激活时，链接元素自动设置一个表示激活的 CSS 类名。

```vue
<router-link to="/">Home</router-link>
```



#### router-view

- `<router-view>` 组件是一个 functional 组件，渲染路径匹配到的视图组件。`<router-view>` 渲染的组件还可以内嵌自己的 `<router-view>`，根据嵌套路径，渲染嵌套组件。
- 其他属性 (非 router-view 使用的属性) 都直接传给渲染的组件， 很多时候，每个路由的数据都是包含在路由参数中。
- 因为它也是个组件，所以可以配合 `<transition>` 和 `<keep-alive>` 使用。如果两个结合一起用，要确保在内层使用 `<keep-alive>`：

```vue
<router-view/>
```



## 嵌套路由

```js
const router = new VueRouter({
  routes: [
    {
      path: '/user/:id',
      component: User,
      children: [
        {
          // 当 /user/:id/profile 匹配成功，
          // UserProfile 会被渲染在 User 的 <router-view> 中
          path: 'profile',
          component: UserProfile
        },
        {
          // 当 /user/:id/posts 匹配成功
          // UserPosts 会被渲染在 User 的 <router-view> 中
          path: 'posts',
          component: UserPosts
        }
      ]
    }
  ]
})
```



## 重定向和别名

### 重定向

- 重定向也是通过 `routes` 配置来完成

```js
// 从 /a 重定向到 /b：
const router = new VueRouter({
  routes: [
    { path: '/a', redirect: '/b' }
  ]
})
```

```js
// 重定向的目标也可以是一个命名的路由：
const router = new VueRouter({
  routes: [
    { path: '/a', redirect: { name: 'foo' }}
  ]
})
```

```js
// 甚至是一个方法，动态返回重定向目标：
const router = new VueRouter({
  routes: [
    { path: '/a', redirect: to => {
      // 方法接收 目标路由 作为参数(to.params to.query)
      // return 重定向的 字符串路径/路径对象
    }}
  ]
})
```



### 别名

```js
// /a 的别名是 /b，意味着，当用户访问 /b 时，URL 会保持为 /b，但是路由匹配则为 /a，就像用户访问 /a 一样。
const router = new VueRouter({
  routes: [
    { path: '/a', component: A, alias: '/b' }
  ]
})
```



## 参数传递

#### params参数

```vue
<router-link  :to="/user/666/555">666666</router-link>
```

```js
const router = new VueRouter({
  routes: [
    {
      path: '/user/:id/:name',
      component: User,
    }
  ]
})
```

```vue
<template>
    <div>
		{{$route.params.id}}	<!-- 666 -->
        {{$route.params.name}}	<!-- 555 -->
    </div>
</template>

<script>
export default {
    name:"",
}
</script>
```



#### query参数

```vue
<router-link  to="/user?id=666&name=555">666666</router-link>
<router-link  :to="{path:'/user',query:{id:666,}}">666666</router-link>
```

```js
const router = new VueRouter({
  routes: [
    {
      path: '/user',
      component: User,
    }
  ]
})
```

```vue
<template>
    <div>
		{{$route.query.id}}
        {{$route.query.name}}
    </div>
</template>

<script>
export default {
    name:"",
}
</script>
```



## 导航守卫

`vue-router` 提供的导航守卫主要用来通过**跳转**或**取消**的方式守卫导航

### 全局前置守卫

```js
const router = new VueRouter({ ... })

router.beforeEach((to, from, next) => {
  // ...
})
```

每个守卫方法接收三个参数：

- **`to: Route`**: 即将要进入的目标 **路由对象**
- **`from: Route`**: 当前导航正要离开的路由
- **`next: Function`**: 一定要调用该方法来 **resolve** 这个钩子。执行效果依赖 `next` 方法的调用参数。
  - **`next()`**: 进行管道中的下一个钩子。如果全部钩子执行完了，则导航的状态就是 **confirmed** (确认的)。
  - **`next(false)`**: 中断当前的导航。如果浏览器的 URL 改变了 (可能是用户手动或者浏览器后退按钮)，那么 URL 地址会重置到 `from` 路由对应的地址。
  - **`next('/')` 或者 `next({ path: '/' })`**: 跳转到一个不同的地址。当前的导航被中断，然后进行一个新的导航。你可以向 `next` 传递任意位置对象，且允许设置诸如 `replace: true`、`name: 'home'` 之类的选项以及任何用在 `router-link` 的 `to` prop或`router-push` 中的选项。
  - **`next(error)`**: (2.4.0+) 如果传入 `next` 的参数是一个 `Error` 实例，则导航会被终止且该错误会被传递给 `router.onError()` 注册过的回调。

**确保 `next` 函数在任何给定的导航守卫中都被严格调用一次。它可以出现多于一次，但是只能在所有的逻辑路径都不重叠的情况下，否则钩子永远都不会被解析或报错**。



###  全局解析守卫

> 2.5.0 新增

- 在 2.5.0+ 可以用 `router.beforeResolve` 注册一个全局守卫
- 这和 `router.beforeEach` 类似，区别是在导航被确认之前，**同时在所有组件内守卫和异步路由组件被解析之后**，解析守卫就被调用。





### 全局后置钩子

- 和守卫不同的是，这些钩子不会接受 `next` 函数也不会改变导航本身：





### 路由独享的守卫

- 可以在路由配置上直接定义 `beforeEnter` 守卫

```js
const router = new VueRouter({
  routes: [
    {
      path: '/foo',
      component: Foo,
      beforeEnter: (to, from, next) => {
        // ...
      }
    }
  ]
})
```



### 组件内的守卫

可以在路由组件内直接定义以下路由导航守卫：

- `beforeRouteEnter`
- `beforeRouteUpdate` (2.2 新增)
- `beforeRouteLeave`

```js
const Foo = {
  template: `...`,
  beforeRouteEnter(to, from, next) {
    // 在渲染该组件的对应路由被 confirm 前调用
    // 不！能！获取组件实例 `this`
    // 因为当守卫执行前，组件实例还没被创建
  },
  beforeRouteUpdate(to, from, next) {
    // 在当前路由改变，但是该组件被复用时调用
    // 举例来说，对于一个带有动态参数的路径 /foo/:id，在 /foo/1 和 /foo/2 之间跳转的时候，
    // 由于会渲染同样的 Foo 组件，因此组件实例会被复用。而这个钩子就会在这个情况下被调用。
    // 可以访问组件实例 `this`
  },
  beforeRouteLeave(to, from, next) {
    // 导航离开该组件的对应路由时调用
    // 可以访问组件实例 `this`
  }
}
```

- `beforeRouteEnter` 守卫 **不能** 访问 `this`，因为守卫在导航确认前被调用，因此即将登场的新组件还没被创建。
- 不过，可以通过传一个回调给 `next`来访问组件实例。在导航被确认的时候执行回调，并且把组件实例作为回调方法的参数。

### 完整的导航解析流程

1. 导航被触发。
2. 在失活的组件里调用 `beforeRouteLeave` 守卫。
3. 调用全局的 `beforeEach` 守卫。
4. 在重用的组件里调用 `beforeRouteUpdate` 守卫 (2.2+)。
5. 在路由配置里调用 `beforeEnter`。
6. 解析异步路由组件。
7. 在被激活的组件里调用 `beforeRouteEnter`。
8. 调用全局的 `beforeResolve` 守卫 (2.5+)。
9. 导航被确认。
10. 调用全局的 `afterEach` 钩子。
11. 触发 DOM 更新。
12. 调用 `beforeRouteEnter` 守卫中传给 `next` 的回调函数，创建好的组件实例会作为回调函数的参数传入。





## 历史模式

在创建路由器实例时，`history` 配置允许我们在不同的历史模式中进行选择



### Hash 模式

- 它在内部传递的实际 URL 之前使用了一个哈希字符（`#`）
- 通过`window.onhashchange`监听到hash的改变，从而处理路由
- 仅 hash 符号之前的内容会被包含在请求中，因此对于后端来说，即使没有做到对路由的全覆盖，也不会返回 404 错误。
- hash兼容`IE8`以上
- SEO不友好

```javascript
import { createRouter, createWebHashHistory } from 'vue-router'

const router = createRouter({
  history: createWebHashHistory(),
  routes: [
    //...
  ],
})
```



###  HTML5 模式

- 直接访问**嵌套路由**会报错，需加**回退路由**
- 利用了 HTML5 History Interface 中新增的 pushState() 和 replaceState() 方法
- history模式需要后端配合将所有访问都指向index.html，否则用户刷新页面，会导致404错误
- history兼容`IE10`以上
- Requires proper server setup for index fallback in production(需要为生产中的索引回退进行适当的服务器设置)

```javascript
import { createRouter, createWebHistory } from 'vue-router'

const router = createRouter({
  history: createWebHistory(),
  routes: [
    //...
  ],
})
```



### Memory模式

- 主要目的是处理SSR
- 没有url
- 存在内存里(如localstroge)

```js
import { createRouter, createMemoryHistory } from 'vue-router'

const router = createRouter({
  history: createMemoryHistory(),
  routes: [
    //...
  ],
})
```





























```javascript
//修改首页路由重复点击报错（重写push方法，添加错误处理）
//（若用replace，将push换为replace）
const VueRouterPush = VueRouter.prototype.push
VueRouter.prototype.push = function push (to) {
  return VueRouterPush.call(this, to).catch(err => err)
}

```

https://s1.hdslb.com/bfs/static/jinkela/international-home/assets/icon_slide_selected.png







# vuex

  Vuex 是一个专为 Vue.js 应用程序开发的**状态管理模式**。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。

![](https://vuex.vuejs.org/vuex.png)

## Store 构造器选项

###  State

```js
// src/store/index.js
import { createStore } from 'vuex'

export default createStore({
  state: {
    count:55
    // {{$store.state.count}}
  },
  mutations: {
  },
  actions: {
  },
  modules: {
  }
})
```





### Getter

- 可以认为是 store 的**计算属性**
- 参数接收
  - Getter接受 state 作为其第一个参数
  - Getter也可以接受其他 getter 作为第二个参数：



#### 通过属性访问

```js
const store = new Vuex.Store({
  state: {
    todos: [
      { id: 1, text: '...', done: true },
      { id: 2, text: '...', done: false }
    ]
  },
  getters: {
    doneTodos: state => {
      return state.todos.filter(todo => todo.done)
    }
  }
})
```



```js
getters: {
  // ...
  doneTodosCount: (state, getters) => {
    return getters.doneTodos.length
  }
```

```js
computed: {
  doneTodosCount () {
    return this.$store.getters.doneTodosCount
  }
}
```



#### 通过方法访问

- 可以通过让 getter 返回一个函数，来实现给 getter 传参

```js
getters: {
  // ...
  getTodoById: (state) => (id) => {
    return state.todos.find(todo => todo.id === id)
  }
}
```

```js
store.getters.getTodoById(2) // -> { id: 2, text: '...', done: false }
```



### Mutation

- 更改 Vuex 的 store 中的状态的唯一方法是提交 mutation(通过`commit`)。
- Vuex 中的 mutation 非常类似于事件：每个 mutation 都有一个字符串的 **事件类型 (type)** 和 一个 **回调函数 (handler)**。这个回调函数就是我们实际进行状态更改的地方，并且它会接受 state 作为第一个参数：


```js
const store = new Vuex.Store({
  state: {
    count: 1
  },
  mutations: {
    increment (state,n) {
      // 变更状态
      // $store.commit('increment',10)
      state.count+=n
    }
  }
})
```



### Action

- Action 类似于 mutation，不同在于：
  - Action 提交的是 mutation，而不是直接变更状态。
  - Action 可以包含任意**异步**操作。
- Action 函数接受一个与 store 实例具有相同方法和属性的 context 对象，因此可以调用 `context.commit` 提交一个 mutation，或者通过 `context.state` 和 `context.getters` 来获取 state 和 getters(可用**解构赋值**)
- Action 通过 `store.dispatch` 方法触发
- Actions 支持同样的载荷方式和对象方式进行分发：

```js
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

```js
actions: {
  actionA ({ commit }) {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        commit('someMutation')
        resolve()
      }, 1000)
    })
  }
}
```

```js
// 假设 getData() 和 getOtherData() 返回的是 Promise

actions: {
  async actionA ({ commit }) {
    commit('gotData', await getData())
  },
  async actionB ({ dispatch, commit }) {
    await dispatch('actionA') // 等待 actionA 完成
    commit('gotOtherData', await getOtherData())
  }
}
```







###  Module

- Vuex 允许我们将 store 分割成**模块（module）**。每个模块拥有自己的 state、mutation、action、getter、甚至是嵌套子模块——从上至下进行同样方式的分割

```js
const moduleA = {
  state: () => ({ ... }),
  mutations: { ... },
  actions: { ... },
  getters: { ... }
}

const moduleB = {
  state: () => ({ ... }),
  mutations: { ... },
  actions: { ... }
}

const store = new Vuex.Store({
  modules: {
    a: moduleA,
    b: moduleB
  }
})

store.state.a // -> moduleA 的状态
store.state.b // -> moduleB 的状态
```

#### 模块内调用根节点

- 对于模块内部的 mutation 和 getter，接收的第一个参数是**模块的局部状态对象**

- `rootState` 和 `rootGetters` 会作为第三和第四参数传入 getter，也会通过 `context` 对象的属性传入 action

  ```js
  const moduleA = {
    // ...
    actions: {
      incrementIfOddOnRootSum ({ state, commit, rootState }) {
        if ((state.count + rootState.count) % 2 === 1) {
          commit('increment')
        }
      }
    }
  }
  ```

- 对于模块内部的 getter，根节点状态会作为第三个参数暴露出来

  ```js
  const moduleA = {
    // ...
    getters: {
      sumWithRootCount (state, getters, rootState) {
        return state.count + rootState.count
      }
    }
  }
  ```

#### 使用模块

- 模块的`state`作为对象加入父节点的`state`中
- 模块的`getters`, `mutation`,`action`直接注册在**全局命名空间**
- 这样使得多个模块能够对同一个 action 或 mutation 作出响应,两个相同的 getter 导致错误
- 可以通过添加 `namespaced: true` 的方式使其成为带命名空间的模块。当模块被注册后，它的所有 getter、action 及 mutation 都会自动根据模块注册的路径调整命名



#### 命名空间

```js
const store = new Vuex.Store({
  modules: {
    account: {
      namespaced: true,
      // 模块内容（module assets）
      state: () => ({ ... }), // 模块内的状态已经是嵌套的了，使用 `namespaced` 属性不会对其产生影响
      getters: {
        isAdmin () { ... } // -> getters['account/isAdmin']
      },
      actions: {
        login () { ... } // -> dispatch('account/login')
      },
      mutations: {
        login () { ... } // -> commit('account/login')
      },

      // 嵌套模块
      modules: {
        // 继承父模块的命名空间
        myPage: {
          state: () => ({ ... }),
          getters: {
            profile () { ... } // -> getters['account/profile']
          }
        },

        // 进一步嵌套命名空间
        posts: {
          namespaced: true,

          state: () => ({ ... }),
          getters: {
            popular () { ... } // -> getters['account/posts/popular']
          }
        }
      }
    }
  }
})
```

















## Store 实例属性

### state

- 类型: `Object`

  根状态，只读。

### getters

- 类型: `Object`

  暴露出注册的 getter，只读

  

## Store 实例方法

### commit

- `commit(type: string, payload?: any, options?: Object)`

- `commit(mutation: Object, options?: Object)`

  提交 mutation。`options` 里可以有 `root: true`，它允许在命名空间模块里提交根的 mutation

```js
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

```js
store.commit('increment')
```

- #### 提交载荷（Payload）

  ```js
  // ...
  mutations: {
    increment (state, n) {
      state.count += n
    }
  }
  ```

  ```js
  store.commit('increment', 10)
  ```

- #### 载荷是一个对象

  ```js
  // ...
  mutations: {
    increment (state, payload) {
      state.count += payload.amount
    }
  }
  ```

  ```js
  store.commit('increment', {
    amount: 10
  })
  ```

- ###  对象风格的提交方式

  ```js
  store.commit({
    type: 'increment',
    amount: 10
  })
  ```

  ```js
  mutations: {
    increment (state, payload) {
      state.count += payload.amount
    }
  }
  ```

  

### dispatch

-  `store.dispatch` 可以处理被触发的 action 的处理函数返回的 Promise，并且 `store.dispatch` 仍旧返回 Promise
- Actions 支持同样的载荷方式和对象方式进行分发

```js
// 以载荷形式分发
store.dispatch('incrementAsync', {
  amount: 10
})

// 以对象形式分发
store.dispatch({
  type: 'incrementAsync',
  amount: 10
})
```



```js
actions: {
  actionA ({ commit }) {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        commit('someMutation')
        resolve()
      }, 1000)
    })
  }
}
```

```js
store.dispatch('actionA').then(() => {
  // ...
})
```



## 组合式API

```js
import { useStore } from 'vuex'

export default {
  setup () {
    const store = useStore()
  }
}
```



