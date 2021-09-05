<template>
  <div class="app">
    <div><button @click="isShow = !isShow">显示/隐藏</button></div>
    <transition class="title" name="bounce">
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
.app {
  width: 200px;
  margin: 0 auto;
}
.title {
  display: inline-block;
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