- ```html
  <script src="https://unpkg.com/vue@next"></script>
  ```

- CDN的全称是Content Delivery Network，即内容分发网络。其基本思路是尽可能避开互联网上有可能影响数据传输速度和稳定性的瓶颈和环节，使内容传输的更快、更稳定。通过在网络各处放置节点服务器所构成的在现有的互联网基础之上的一层智能虚拟网络，CDN系统能够实时地根据网络流量和各节点的连接、负载状况以及到用户的距离和响应时间等综合信息将用户的请求重新导向离用户最近的服务节点上。其目的是使用户可就近取得所需内容，解决 Internet网络拥挤的状况，提高用户访问网站的响应速度

- npm,Node Package Manager,node包管理器，是程序员Isaaz开发的用于集中管理代码的工具。现在用 npm 来分享代码已经成了前端的标配

- CLI,Command-line interface,命令行界面，命令行工具

- Vue 和 React 的相同点

  - 利用虚拟DOM实现快速渲染
  - 轻量级
  - 响应式组件
  - 支持服务器端渲染
  - 易于集成路由工具、打包工具以及状态管理工具

  PS：Vue 在国内很受欢迎；React 在国内和国外都很受欢迎，适合做大型网站。

- 虚拟DOM:在JS内存中构建类似于DOM的对象，去拼装数据，拼装完整后把数据整体解析，一次性插入到HTML中，这样就形成了虚拟DOM

- Vue框架的特点

  - 模板渲染：基于 html 的模板语法，学习成本低。
  - 响应式的更新机制：数据改变之后，视图会自动刷新。【重要】
  - 渐进式框架
  - 组件化/模块化
  - 轻量：开启 gzip压缩后，可以达到 20kb 大小。（React 达到 35kb，AngularJS 达到60kb）。

- 元编程metaprogramming:框架作者使用一种编程语言固有的语言特性，创造出相对新的语言特性，使得最终使用者能以新语法和语义来构建它们的应用程序从而在某些领域开发中获得更好的效果。

- v-bind 绑定元素的属性attribute  

- v-on,事件监听器，通过它调用在实例中定义的方法。

- v-model,实现表单输入和应用状态之间的双向绑定。

- v-if,控制一个元素是否显示

- v-for,绑定数组的数据来渲染一个项目列表。

- 组件系统是 Vue 的另一个重要概念，因为它是一种抽象，允许我们使用小型、独立和通常可复用的组件构建大型应用。仔细想想，几乎任意类型的应用界面都可以抽象为一个组件树。

- 跟组件、挂载   mount()不返回应用本身，返回的是根组件实例。

- vm:ViewModel,表示组件实例，每个组件都有自己的组件实例vm，对于一些组件，如TodoItem,在任何时候都可能有多个实例渲染，这些应用中的所有组件实例将共享一个应用实例。

- 每个 Vue 应用都是通过用 `createApp` 函数创建一个新的**应用实例**开始的，该应用实例是用来在应用中注册“全局”组件的

  - ```js
    经典eg:
    //html:
    <div id="hello-vue" class="demo">
      {{ message }}
    </div>
    
    //js
    const HelloVueApp = {
      data() {
        return {
          message: 'Hello Vue!!'
        }
      }
    }
    
    Vue.createApp(HelloVueApp).mount('#hello-vue')
    
    
    const app = Vue.createApp({})  //此时app为应用实例vm
        const RootComponent = { 
      /* 选项 */ 
    }
    const app = Vue.createApp(RootComponent)  //传递给 createApp 的选项用于配置根组件，也就是此时RootComponent为根组件，根组件是挂载应用时渲染的起点。大多数真实应用都是组件树
    const vm = app.mount('#app')  //此时mount挂载id为app的html
    //data，methods，props，computed，inject 和 setup这些称为property，组件实例的所有property都可以在组件模板访问，Vue的内置property如$attrs 前面会有$符号用于区分。
    ```

#### 1.挂载mount

- 挂载的内部可使用任意多个标签，
- 可以挂载任意选择器，但一般都使用id选择器，因为id选择器是唯一的。
- 支持大多数标签，body和html除外。

#### 2.data 数据对象

- Vue用到的数据定义在data中
- data中可以写复杂类型的数据
- 渲染复杂类型数据时遵守JS语法即可。

#### 3.Vue指令

- 1.内容绑定，事件绑定  v-html v-on基础 v-text
- 显示切换，属性绑定 v-show v-if v-bind
- 列表循环 ，表单元素绑定 v-for  v-on补充 v-model

#### 4.v-text  用于设置标签的文本值

```js
  <div id = 'dd' >
    <h2 v-text = 'message'>11111</h2>
    <h3 v-text = 'message'></h3>
  </div>

  <script src="https://unpkg.com/vue@next"></script>

  <script>
    const appdd = {
      data() {
        return {
          message:'确实帅'
        }
      }
    }
   Vue.createApp(appdd).mount('#dd');
</script>
```

- 作用是设置标签的内容
- 默认写法会替换全部内容，使用差值表达式可以替换指定内容
- 内部支持写表达式

#### 5.v-html

- 设置标签的innerHTML，内容中有html的结构会被解析为标签
- 如果是普通文本则效果和v-text相同

#### 6.v-on

- 用于为元素绑定事件

- 绑定的方法定义在methods属性中

- 方法内部通过this关键字可以访问定义在data中数据

- ```js
  <div>
  <input type='button' value='事件绑定' v-on:click = 'dolt'>
  <input type='button' value='事件绑定' v-on:mouseenter = 'dolt'>
  <input type='button' value='事件绑定' v-on:dbclick = 'dolt'>
  </div>
  
  v-on可缩写为@
  <input type='button' value='事件绑定' @dbclick = 'dolt'>
  
  //实例
    <div id="app">
      <button @click='tttt'>点我</button>
    </div>
  
    <script src="https://unpkg.com/vue@next"></script>
  
    <script>
      const appdd = {
        data() {
          return {
            message:'确实帅'
          }
        },
        methods: {
          tttt(){
            alert('你是真的帅！')
          }
        },
      }
     Vue.createApp(appdd).mount('#app');
  ```

- 传递自定义参数  @click = 'doit(p1,p2)'
- 事件修饰符  @keyup.enter = 'sayhi'   事件修饰符有许多种，可在官网查

#### 7.v-show

- 根据表达式的真假，切换元素的显示和隐藏，表达式的内容最终会被解析为布尔值

- 注意是truthy而不是true，当值为负数时也会显示

- 原理是修改元素的display，实现显示或者隐藏

- ```js
    <div id="app">
      <img v-show = 'tat' src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fgss0.baidu.com%2F94o3dSag_xI4khGko9WTAnF6hhy%2Fzhidao%2Fpic%2Fitem%2F267f9e2f0708283867bc7d5fb599a9014d08f1cc.jpg&refer=http%3A%2F%2Fgss0.baidu.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1643961881&t=12ac6a72fb9ea7a9c9cdba728b4a1717" alt="希里">
    </div>
    <script src="https://unpkg.com/vue@next"></script>
    <script>
      const app = {
        data() {
          return {
            tat:-1
          }
        },
        
      }
      Vue.createApp(app).mount('#app')
  ```

#### 8.v-if

- 根据表达式真假，切换元素显示或隐藏，操纵的是dom元素
- 与v-show不同的是它会完全隐藏dom元素，而v-show只是修改了display属性
- 实际使用时频繁切换的用v-show,反之用v-if

#### 9.v-bind 

- 用于设置元素的属性，比如src,title,class
- 语法:v-bind:属性名 = 表达式   缩写   :属性名 = 表达式

#### 10.图片切换

- 列表数据使用数组保存
- v-bind用于设置src 
- v-show和v-if都可以切换元素的显示状态

#### 11.v-for

- 根据数据生成列表结构
- 数据经常和v-for结合使用
- 语法是(item,index) in 数据
- 数组长度更新是响应式的
- ![image-20220109201459361](http://typora888.oss-cn-beijing.aliyuncs.com/img/image-20220109201459361.png)

#### 12.v-model 

- 获取和设置表单元素的值(双向数据绑定)

- ```js
   <div id="app">
      <input type="text" v-model = 'message' placeholder="快写!">
      <p>{{message}}确实帅</p>
    </div>
    <script src="https://unpkg.com/vue@next"></script>
    <script>
       const app = {
         data() {
           return {
             message:'hello southsky'
           }
         },
       }
       Vue.createApp(app).mount('#app')
    </script>
  ```

### 案例:记事本

- 功能:
  -  新增
  - 删除
  - 统计
  - 清空
  - 隐藏

#### 生命周期钩子

- 用于给用户在不同阶段添加自己代码的机会，如created,mounted,updated,unmounted,生命周期钩子的this指向调用它的当前活动实例。
- 不要在选项property或回调上调用箭头函数，箭头函数没有this。

#### 文本

- 数据绑定最常用方式就是使用Mustache双大括号语法的文本插值

- ```js
  <div>Message:{{msg}}</div>
  //此时Mustache即双大括号内的值会被替代为组件实例中msg property的值，并且会实时更新。
  <span v-once>这个将不会改变: {{ msg }}</span> 
  //通过v-once指令可以执行一次性插值，数据改变时msg不会更新。
  ```

#### 原始html

- 双大括号会将数据解释为普通文本，为了输出真正html，需要使用v-html指令。

#### Truthy和falsy

在 [JavaScript](https://developer.mozilla.org/zh-CN/docs/Glossary/JavaScript) 中，**truthy**（真值）指的是在[布尔值](https://developer.mozilla.org/zh-CN/docs/Glossary/Boolean)上下文中，转换后的值为真的值。所有值都是真值，除非它们被定义为 [假值](https://developer.mozilla.org/zh-CN/docs/Glossary/Falsy)（即除 `false`、`0`、`-0`、`0n`、`""`、`null`、`undefined` 和 `NaN` 以外皆为真值）

#### Attribute  还未理解

#### JS表达式

#### 指令

- 指令Directives是带有v-前缀的特殊attribute,其值预期是单个JS表达式(v-for和v-on除外)，指令的职责是表达式的值改变时，将其产生的连带影响响应式的作用于DOM

#### 动态参数

- 可在指令参数中使用JS表达式，方法是用方括号括起来。

- ```js
  <a v-bind:[attributeName]="url"> ... </a>
  ```

#### 修饰符

- 修饰符 (modifier) 是以半角句号 `.` 指明的特殊后缀，用于指出一个指令应该以特殊方式绑定。例如，`.prevent` 修饰符告诉 `v-on` 指令对于触发的事件调用 `event.preventDefault()`：

- ```js
  <form v-on:submit.prevent="onSubmit">...</form>
  ```

#### 缩写

- V-bind缩写

  ```html
  <!-- 完整语法 -->
  <a v-bind:href="url"> ... </a>
  
  <!-- 缩写 -->
  <a :href="url"> ... </a>
  
  <!-- 动态参数的缩写 -->
  <a :[key]="url"> ... </a>
  ```

- V-on缩写

- ```html
  <!-- 完整语法 -->
  <a v-on:click="doSomething"> ... </a>
  
  <!-- 缩写 -->
  <a @click="doSomething"> ... </a>
  
  <!-- 动态参数的缩写 -->
  <a @[event]="doSomething"> ... </a>
  ```

### 计算属性

- 对于任何包含响应时数据的复杂逻辑，都应该使用计算属性。
- 我们可以将同样的函数定义为一个方法，而不是一个计算属性。从最终结果来说，这两种实现方式确实是完全相同的。然而，不同的是**计算属性将基于它们的响应依赖关系缓存**。计算属性只会在相关响应式依赖发生改变时重新求值。这就意味着只要 `author.books` 还没有发生改变，多次访问 `publishedBookMessage` 时计算属性会立即返回之前的计算结果，而不必再次执行函数
- 计算属性默认只有getter，但可以自定义setter

### 侦听器、侦听属性

- 虽然计算属性在大多数情况下更合适，但有时也需要一个自定义的侦听器。这就是为什么 Vue 通过 `watch` 选项提供了一个更通用的方法来响应数据的变化。当需要在数据变化时执行异步或开销较大的操作时，这个方式是最有用的。

#### 条件渲染

- v-else必须紧跟在v-if后，否则不会被识别，v-if-else同理,v-if-else可以连续使用

- ```js
  <div v-if="Math.random() > 0.5">
    Now you see me
  </div>
  <div v-else>
    Now you don't
  </div>
  
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

- `v-if` 是“真正”的条件渲染，因为它会确保在切换过程中，条件块内的事件监听器和子组件适当地被销毁和重建。

  `v-if` 也是**惰性的**：如果在初始渲染时条件为假，则什么也不做——直到条件第一次变为真时，才会开始渲染条件块。一般来说，`v-if` 有更高的切换开销，而 `v-show` 有更高的初始渲染开销。因此，如果需要非常频繁地切换，则使用 `v-show` 较好；如果在运行时条件很少改变，则使用 `v-if` 较好

### 列表渲染

- v-for,基于一个数组来渲染一个列表，需要使用item in items形式的特殊语法，items是源数组，item是被迭代的数组元素的别名。

- v-for可以访问所有父作用域的property,v-for还支持第二个可选参数，索引。

- ```js
  <li v-for="(item, index) in items"> 
  //v-for支持in和of作分隔符，二者等效。
  <li v-for="item in items">  
  <div v-for="item of items"></div>
  ```

- v-for可用于遍历一个对象的property

- ```js
  <li v-for="value in myObject">
      {{ value }}
      
  //也可提供property名称(即键名key)
  <li v-for="(value, name) in myObject">
    {{ name }}: {{ value }}
  </li>
  ```

- v-for采用就地更新的策略，若如果数据项的顺序被改变，Vue 将不会移动 DOM 元素来匹配数据项的顺序，而是就地更新每个元素，并且确保它们在每个索引位置正确渲染。

- 这个默认的模式是高效的，但是**只适用于不依赖子组件状态或临时 DOM 状态 (例如：表单输入值) 的列表渲染输出**。为了给 Vue 一个提示，以便它能跟踪每个节点的身份，从而重用和重新排序现有元素，你需要为每项提供一个唯一的 `key` attribute：

- ```html
  <div v-for="item in items" :key="item.id">
    <!-- 内容 -->
  </div>
  ```

- v-if优先级高于v-for。

### 监听事件

- v-on(缩写为@)来监听DOM事件，并在触发事件时执行JS，用法为v-on:click = 'methodName'或@click = 'methodName'
- 在事件处理程序中调用 `event.preventDefault()` 或 `event.stopPropagation()` 是非常常见的需求。尽管我们可以在方法中轻松实现这点，但更好的方式是：方法只有纯粹的数据逻辑，而不是去处理 DOM 事件细节。
- 为了解决这个问题，Vue.js 为 `v-on` 提供了**事件修饰符**。之前提过，修饰符是由点开头的指令后缀来表示的。
  - `.stop`
  - `.prevent`
  - `.capture`
  - `.self`
  - `.once`
  - `.passive`

### 按键修饰符

- #### 按键别名

  - `.enter`
  - `.tab`
  - `.delete` (捕获“删除”和“退格”键)
  - `.esc`
  - `.space`
  - `.up`
  - `.down`
  - `.left`
  - `.right`

- `.exact` 修饰符允许你控制由精确的系统修饰符组合触发的事件

### 表单输入绑定

- v-model 指令在表单 `<input>`、`<textarea>` 及 `<select>` 元素上创建双向数据绑定.它会根据控件类型自动选取正确的方法来更新元素

### 组件

- 带有名称的可复用实例

- ```js
  // Create a Vue application
  const app = Vue.createApp({})
  
  // Define a new global component called button-counter
  app.component('button-counter', {   //此时组件是button-counter
    data() {
      return {
        count: 0
      }
    },
    template: `
      <button v-on:click="count++">
        You clicked me {{ count }} times.
      </button>`
  })
  
  app.mount('#components-demo')
  ```

- 组件可以任意次数的复用

- 为了能在模板中使用，组件必须先注册以便Vue识别，注册有两种类型:全局注册和局部注册，全局注册通过component进行

  - ```
    const app = Vue.createApp({});
    app.component('my-component-name',{
    //..选项..
    })
    ```

  - 全局注册的组件可在应用中的任何组件模板中使用。