<template>
  <div class="app">
    <div><button @click="isShow = !isShow">显示/隐藏</button></div>

    <!-- 
      可以在 attribute 中声明 JavaScript 钩子
     -->
    <transition
      @before-enter="beforeEnter"
      @enter="enter"
      @after-enter="afterEnter"
      @enter-cancelled="enterCancelled"
      @before-leave="beforeLeave"
      @leave="leave"
      @after-leave="afterLeave"
      @leave-cancelled="leaveCancelled"
    >
      <h2 class="title" v-if="isShow">Hello World</h2>
    </transition>
  </div>
</template>

<script>
import gsap from 'gsap';
export default {
  data() {
    return {
      isShow: true,
    }
  },
  methods: {
    // 当与 CSS 结合使用时
    // 回调函数 done 是可选的
    enter(el, done) {
      gsap.from(el, {
        scale: 0,
        x: 200,
        onComplate: done
      })
    },
    // 当与 CSS 结合使用时
    // 回调函数 done 是可选的
    leave(el, done) {
     gsap.to(el, {
        scale: 0,
        x: 200,
        onComplate: done
      })
    },
  },
}
</script>

<style scoped>
.title {
  display: inline-block;
}
</style>
