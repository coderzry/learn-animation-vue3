<template>
  <div class="app">
    <div><button @click="isShow = !isShow">显示/隐藏</button></div>

    <!-- transition自定义过渡类名
        更多自定义类名参考文档： https://v3.cn.vuejs.org/guide/transitions-enterleave.html#%E8%87%AA%E5%AE%9A%E4%B9%89%E8%BF%87%E6%B8%A1-class-%E7%B1%BB%E5%90%8D
     -->
     <!-- animate__animated类必须加上 第二个类为具体动画名称-->
    <transition enter-active-class="animate__animated animate__fadeInDown"
                leave-active-class="animate__animated animate__fadeOutRight">
      <h2 class="title" v-if="isShow">Hello World</h2>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isShow: true,
    }
  },
}
</script>

<style scoped>
.title {
  display: inline-block;
}

/* 还可以重写动画反转 */
.animate__fadeOutRight {
  animation-direction: reverse;
}

/* transition自带的过渡类名 */
/* .bounce-enter-active {
  animation: bounceInUp 1s ease-in;
}

.bounce-leave-active {
  animation: bounceInUp 1s ease-in reverse;
} */
</style>
