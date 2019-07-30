<template>
  <div>
    <header>first vue demo</header>
    <section class="game-body">
      <section class="row row-1">
        <GameLi class="row-one" @liClick="handleOuterClick(0)" v-bind:text="checkText"/>
        <GameLi class="row-one" @liClick="handleOuterClick(1)" v-bind:text="checkText"/>
        <GameLi class="row-one" @liClick="handleOuterClick(2)" v-bind:text="checkText"/>
      </section>
      <section class="row row-2">
        <GameLi class="row-one" @liClick="handleOuterClick(3)" v-bind:text="checkText"/>
        <GameLi class="row-one" @liClick="handleOuterClick(4)" v-bind:text="checkText"/>
        <GameLi class="row-one" @liClick="handleOuterClick(5)" v-bind:text="checkText"/>
      </section>
      <section class="row row-3">
        <GameLi class="row-one" @liClick="handleOuterClick(6)" v-bind:text="checkText"/>
        <GameLi class="row-one" @liClick="handleOuterClick(7)" v-bind:text="checkText"/>
        <GameLi class="row-one" @liClick="handleOuterClick(8)" v-bind:text="checkText"/>
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
      checkText: true,
      count: 0,
      gameOver: false,
      gameMp: [
        [null, null, null],
        [null, null, null],
        [null, null, null]
      ]
    }
  },
  methods: {
    handleOuterClick (index) {
      if (this.count >= 5) {
        this.checkRules()
        if (this.gameOver) {
          return
        }
      }
      //NOTE:  如果填满了格子,还没有分出胜负也进行返回
      if (this.count === 9 && !this.gameOver) {
        return
      }
      console.log('this outer click')
      this.checkText = !this.checkText
      this.count++
    },
    checkRules () {
      //TODO:  规则判断暂时没有做处理
      // let {gameMp} = this
      // let row1 = gameMp[0]
      // let row2 = gameMp[1]
      // let row3 = gameMp[2]
      // this.rule1(row1)
    }
  }
}
</script>

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
  font-size: 50px;
  width: 300px;
  height: 300px;
  position: relative;
  left: 50%;
  transform: translateX(-50%);
}
.row {
  display: flex;
}

.row-1, .row-2{
  border-bottom: 5px solid rgb(72, 158, 146);
}
.row-1 >.row-one:nth-child(1){
  border-top-left-radius: 8px;
  border-right: 5px solid rgb(72, 158, 146);
}
.row-1 >.row-one:nth-child(3){
  border-top-right-radius: 8px;
  border-left: 5px solid rgb(72, 158, 146);
}
.row-2 >.row-one:nth-child(1){
  border-right: 5px solid rgb(72, 158, 146);
}
.row-2 >.row-one:nth-child(3){
  border-left: 5px solid rgb(72, 158, 146);
}
.row-3 >.row-one:nth-child(1){
  border-bottom-left-radius: 8px;
  border-right: 5px solid rgb(72, 158, 146);
}
.row-3 >.row-one:nth-child(3){
  border-bottom-right-radius: 8px;
  border-left: 5px solid rgb(72, 158, 146);
}

</style>
