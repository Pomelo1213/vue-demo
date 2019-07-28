<template>
  <div class="game-li">
    {{text}}
  </div>
</template>

<script>
export default {
  props: ['text'],
  methods () {

  },
  data () {
    return {

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
