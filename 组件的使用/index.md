##### 组件的使用

> 组件是可复用的Vue实例，且带有一个名字。


vue组件的使用步骤分为一下三种步骤：

  1. [组件的创建](#1)

      * 通过字符串(例如:```template: "..."```)的形式来创建组件
      * 通过单文件(```xxx.vue```)的形式来创建组件
      * 通过```<script type="text/x-template"></script>```的形式
      * 通过渲染函数来创建

  2. [组件的注册](#2)
      * 全局注册
      * 局部注册
  3. 组件的使用



##### <div id="1">组件的创建</div>

1. 字符串```template```的方式

```
  <div id="app">
    <base-button></base-button>
  </div>
  <script>
  Vue.component("base-button", {
    template: `
      <button>提交</button>
    `
  })

  const vm = new Vue({
    el: "#app"
  })
  </script>
```

2. 单文件(```xxx.vue```)的形式
```
  // 引入vue-loader
  <script src="https://unpkg.com/http-vue-loader"></script>

  Vue.component("single-base-button", httpVueLoader("SingleBaseButton.vue"))

  // SingleBaseButton.vue文件
  <template>
    <div>
      <button>single</button>
    </div>
  </template>

  <script>
  module.exports = {
    name: "SingleBaseButton"
  }
  </script>

```

3. ```<script type="text/x-template"></script>```的方式
```
  <script type="text/x-template" id="x-template-button">
    <button>x-template</button>
  </script>

  Vue.component("x-base-button", {
    template: "#x-template-button"
  })
```

4. 渲染函数的方式

渲染函数是什么？？

其实在我们使用```vue-cli```来搭建 vue 项目时，绝大多数的情况下，都是通过单文件的形式来创建组件或者```template```来创建 HTML 模板，而对渲染函数的使用就少得可怜。渲染函数更接近```JavaScript```的编程能力，比```template```更接近编译器。

```main.js```文件里面的```render```就是渲染函数： 

```
  new Vue({
    store,
    router,
    render: h => h(App)
  }).$mount("#app")
``` 
4.1 ```render```函数的认识

  * ```render```函数的基本使用

```
  render: function(createElement) {
    return createElement("div", "hello, ljl")
  }
```
  * ```createElement```函数的接受参数






#### <div id="2">组件的注册</div>

1. 全局注册

```
  // 全局注册
  Vue.component("x-base-button", {
    template: "#x-template-button"
  })
```

2. 局部注册

```
  // index.html
  <div id="app">
    <component-part></component-part>
  </div>

  <script>
  // 局部注册
  const ComponentPart = {
    template: `<button>局部注册</button>`
  }
  const vm = new Vue({
    el: "#app",
    components: {
      ComponentPart: ComponentPart
    }
  })
  </script>
```



#### 参考资料

[Vue框架](https://cn.vuejs.org/)


























