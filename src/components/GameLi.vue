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
  color: red;
  width: 100px;
  height: 100px;
  box-sizing: border-box;
  border: 1px solid orange;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
