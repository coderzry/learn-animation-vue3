<template>
  <div class="app">
    <div><button @click="isShow = !isShow">显示/隐藏</button></div>
    <!-- 
      Vue 为了知道过渡的完成，必须设置相应的事件监听器。它可以是 transitionend 或 animationend，
      这取决于给元素应用的 CSS 规则。如果你使用其中任何一种，Vue 能自动识别类型并设置监听。
      但是，在一些场景中，你需要给同一个元素同时设置两种过渡动效，比如 animation 很快的被触发并完成了，而 transition 效果还没结束。
      在这种情况中，你就需要使用 type attribute 并设置 animation 或 transition 来明确声明你需要 Vue 监听的类型。
     -->
     <!-- duration中设置的时间会覆盖css中的时间 -->
    <transition name="bounce" type="transition" :duration="{ enter: 500, leave: 800 }">
      <h2 class="title" v-show="isShow">Hello World</h2>
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
