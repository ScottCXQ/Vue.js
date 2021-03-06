前面已经介绍过许多 Vue 内置的指令，比如 v-if、v-show 等，这些丰富的内置指令能满足我们的绝大多数业务需求，不过在需要一些特殊功能时，我们仍然希望对 DOM 进行底层的操作，这时就需要用到自定义指令。\
自定义指令的注册方法和组件很像，也分为全局注册和局部注册，比如注册一个 v-focus 的指令，两种写法分别是：\
// 全局注册\
Vue.directive('focus', {\
  // 指令选项\
});\
\
// 局部注册\
const app = new Vue({\
  el: '#app',\
  directives: {\
    focus: {\
      // 指令选项      \
    }\
  }\
});\
自定义指令的选项是由几个钩子函数组成的，每个都是可选的：
1. bind：只调用一次，指令第一次绑定到元素时调用，用这个钩子函数可以定义一个在绑定时执行一次的初始化动作。
2. inserted：被绑定元素插入父节点时调用（父节点存在即可调用，不必存在于 document 中）。
3. update：被绑定元素所在的模板更新时调用，而不论绑定值是否变化。通过比较更新前后的绑定值，可以忽略不必要的模板更新。
4. componentUpdated：被绑定元素所在的模板完成一次更新周期时调用。
5. unbind：只调用一次，指令与元素解绑时调用。
