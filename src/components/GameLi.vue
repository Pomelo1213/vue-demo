<template>
  <div v-on:click="handleClick" class="game-li">
    <template v-if="flag">{{check}}</template>
    <template v-else></template>
  </div>
</template>

<script>
export default {
  props: ['text'],
  data () {
    return {
      flag: false
    }
  },
  methods: {
    handleClick () {
      if (this.flag) {
        return
      }
      this.flag = true
      this.check = this.text ? 'o' : 'x'
      this.$emit('liClick')
    }
  }
}

</script>

<style scope>
.game-li {
  color: #fff;
  width: 100px;
  height: 100px;
  box-sizing: border-box;
  border-bottom: 3px solid rgb(72, 158, 146);
  display: flex;
  justify-content: center;
  align-items: center;
  background: #14bdac;
  cursor: pointer;
  user-select: none;
}
.game-li:nth-child(1), .game-li:nth-child(3), .game-li:nth-child(7) {
  border-right: 3px solid rgb(72, 158, 146);
}
.game-li:nth-child(3), .game-li:nth-child(6), .game-li:nth-child(9) {
  border-left: 3px solid rgb(72, 158, 146);
}
.game-li:nth-child(7), .game-li:nth-child(8), .game-li:nth-child(9) {
  border-bottom: transparent;
}
</style>
