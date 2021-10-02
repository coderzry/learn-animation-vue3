<template>
  <div class="app">
    <input type="number" step="100" v-model="counter" />
    <h2>当前计数： {{ showCounter }}</h2>
  </div>
</template>

<script>
import gsap from 'gsap'
export default {
  data() {
    return {
      counter: 0,
      showNumber: 0
    }
  },
  computed: {
    showCounter() {
      return this.showNumber.toFixed(0)
    }
  },
  watch: {
    // gsap实现数字递增效果
    counter(newVal) {
      gsap.to(this, {duration: 1, showNumber: newVal})
    }
  }
}
</script>

<style scoped></style>
