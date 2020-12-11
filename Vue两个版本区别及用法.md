# Vue两个版本区别及用法
1. #### 两个版本对应的文件名

   Vue.js有不同的构建版本，主要分为两种：完整版和运行时非完整版。

   完整版vue文件名通常为：vue.js/vue.common.js / vue.esm.js···

   运行时非完整版vue文件名通常为： vue.runtime.js / vue.runtime.common.js···，非完整版vue文件后面一定会跟runtime。

   完整版包含了编译器，因此完整版比运行时非完整版大30%。

2. #### template 和 render 怎么用

   如果你需要在客户端编译模板 (比如传入一个字符串给 `template` 选项，或挂载到一个元素上并以其 DOM 内部的 HTML 作为模板)，就将需要加上编译器，即完整版：

   ```javascript
   // 完整版运行，需要编译器
   new Vue({
     template: '<div>{{ hi }}</div>'
   })
   ```

   当使用 `vue-loader` 或 `vueify` 的时候，`*.vue` 文件内部的模板会在构建时预编译成 JavaScript。你在最终打好的包里实际上是不需要编译器的，所以只用运行时版本即可。

   ```javascript
   // 运行时非完整版运行，不需要编译器
   new Vue({
     render (h) {
       return h('div', this.hi)
     }
   })
   ```

3. #### 如何用 codesandbox.io 写 Vue 代码

   除了用`vue create xxx`

   这种语句创建vue项目文件之外，也可以登录codesandbox.io网站。不要登录，选择vue，就会自动创建vue文件。

   写完代码选择左上角File——Export to ZIP导出文件到本地。
