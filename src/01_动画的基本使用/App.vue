<template>
  <div>
    <button @click="isShow = !isShow">显示/隐藏</button>
    <!-- 
      使用Vue内置组件 transition 实现过渡效果
      transition中class的命名规则如下：
        如果是没有使用name的transition, 那么所有的class都是以v-开头的
        如果给transition添加了name属性，比如 <transition name="fade">，那么所有的class都会以fade-开头
      
      实现原理：
        当插入或删除包含在 transition 组件中的元素时，Vue 将会做以下处理：

        1.自动嗅探目标元素是否应用了 CSS 过渡或动画，如果是，在恰当的时机添加/删除 CSS 类名。

        2.如果过渡组件提供了 JavaScript 钩子函数，这些钩子函数将在恰当的时机被调用。

        3.如果没有找到 JavaScript 钩子并且也没有检测到 CSS 过渡/动画，DOM 操作 (插入/删除) 在下一帧中立即执行。(注意：此指浏览器逐帧动画机制，和 Vue 的 nextTick 概念不同)
     -->  
    <transition name="fade">
      <h2 v-show="isShow">Hello World</h2>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isShow: true
    }
  },
}
</script>

<style scoped>
  /* 
    元素显示时，enter-from -> enter-to, opacity从 0-1  
    元素隐藏时，leave-from -> leave-to, opacity从 1-0    
  */
  .fade-enter-from,
  .fade-leave-to {
    opacity: 0;
  }

  .fade-enter-to,
  .fade-leave-from {
    opacity: 1;
  }

  /* 
    acitve这个类可以定义 进入/离开过渡的的过渡时间，延迟和曲线函数。
  */
  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 1s ease;
  } 
</style>