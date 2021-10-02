<template>
  <div>
    <button @click="addNum">添加数字</button>
    <button @click="removeNum">删除数字</button>
    <button @click="shuffleNum">数字洗牌</button>

    <transition-group tag="p" name="zry">
      <span class="item" v-for="item in numbers" :key="item">
        {{ item }}
      </span>
    </transition-group>
  </div>
</template>

<script>
import _ from 'lodash'
export default {
  data() {
    return {
      numbers: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
      numCounter: 10
    }
  },
  methods: {
    addNum() {
      // this.numbers.push(this.numCounter++)
      this.numbers.splice(this.randomIndex(), 0, this.numCounter++)
    },
    removeNum() {
      this.numbers.splice(this.randomIndex(), 1)
    },
    randomIndex() {
      return Math.floor(Math.random() * this.numbers.length)
    },
    // 使用lodash实现数组洗牌
    shuffleNum() {
      this.numbers = _.shuffle(this.numbers)
    }
  }
}
</script>

<style>
.item {
  margin-right: 10px;
  display: inline-block;
}

.zry-enter-from,
.zry-leave-to {
  opacity: 0;
  transform: translateY(30px);
}

.zry-enter-active,
.zry-leave-active {
  transition: all 1s ease;
}

.zry-leave-active {
  position: absolute;
}

.zry-move {
  transition: transform 1s ease;
}

</style>