<template>
  <div>
    <header>first vue demo</header>
    <section class="game-body">
      <section class="row">
        <GameLi v-bind:text="checkText"/>
        <GameLi v-bind:text="checkText"/>
        <GameLi v-bind:text="checkText"/>
      </section>
      <section class="row">
        <GameLi v-bind:text="checkText"/>
        <GameLi v-bind:text="checkText"/>
        <GameLi v-bind:text="checkText"/>
      </section>
      <section class="row">
        <GameLi v-bind:text="checkText"/>
        <GameLi v-bind:text="checkText"/>
        <GameLi v-bind:text="checkText"/>
      </section>
    </section>
  </div>
</template>

<script>
import GameLi from '../components/GameLi'
export default {
  name: 'Game',
  components: {
    GameLi
  },
  data () {
    return {
      checkText: 'o',
      gameMp: [
        [],
        [],
        []
      ]

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.game-body {
  border: 1px solid;
  font-size: 50px;
  width: 300px;
  height: 300px;
}
.row {
  display: flex;
}
</style>
