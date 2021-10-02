<template>
  <div>
    <!-- 列表的交错过渡 -->
    <input v-model="query" />
    <transition-group
      tag="ul"
      name="zry"
      :css="false"
      @enter="enter"
      @leave="leave"
      @beforeEnter="beforeEnter"
    >
      <li class="item" v-for="(item, index) in showNames" :key="item" :data-index="index">
        {{ item }}
      </li>
    </transition-group>
  </div>
</template>

<script>
import gsap from 'gsap'
export default {
  data() {
    return {
      names: ['aca', 'asd', 'code', 'jams', 'michael'],
      query: '',
    }
  },
  computed: {
    showNames() {
      return this.names.filter((item) => item.indexOf(this.query) !== -1)
    },
  },
  methods: {
    beforeEnter(el) {
      el.style.opacity = 0
      el.style.height = 0
    },
    enter(el, done) {
      gsap.to(el, {
        opacity: 1,
        height: '1.6em',
        delay: el.dataset.index * 0.15,
        onComplete: done,
      })
    },
    leave(el, done) {
      gsap.to(el, {
        opacity: 0,
        height: 0,
        delay: el.dataset.index * 0.15,
        onComplete: done,
      })
    },
  },
}
</script>

<style>
.zry-enter-from,
.zry-leave-to {
  opacity: 0;
}

.zry-enter-active,
.zry-leave-active {
  transition: opacity 1s ease;
}
</style>
