<template>
  <div class="app">
    <div><button @click="isShow = !isShow">显示/隐藏</button></div>
    <!-- 
      <transition> 的默认行为 - 进入和离开同时发生。
      以下代码执行时，动画进入和离开会同时发生，导致页面过渡效果不好。
      这是 <transition> 的默认行为 - 进入和离开同时发生。
        同时生效的进入和离开的过渡不能满足所有要求，所以 Vue 提供了过渡模式
        in-out：新元素先进行过渡，完成之后当前元素过渡离开。
        out-in：当前元素先进行过渡，完成之后新元素过渡进入。
     -->
    <transition name="bounce" mode="in-out">
      <h2 class="title" v-if="isShow">Hello World</h2>
      <h2 class="title" v-else>你好啊，李银河</h2>
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
.app {
  width: 200px;
  margin: 0 auto;
}
.title {
  display: inline-block;
}

/* 
  transition animation 是可以同时使用的
  如果两者的持续时间不同，需要使用 type attribute 并设置 animation 或 transition 来明确声明你需要 Vue 监听的类型
*/

.bounce-enter-from,
.bounce-leave-to {
  opacity: 0;
}

.bounce-enter-active,
.bounce-leave-active {
  transition: opacity 2s ease;
}

.bounce-enter-active {
  animation: bounce 1s ease;
}

.bounce-leave-active {
  animation: bounce 1s ease reverse;
}

@keyframes bounce {
  0% {
    transform: scale(0);
  }

  50% {
    transform: scale(1.2);
  }

  100% {
    transform: scale(1);
  }
}
</style>
