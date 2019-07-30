<template>
  <div>
    <header>first vue demo</header>
    <button class="reset" @click="handleResetClick">reset</button>
    <section class="game-body">
      <section class="row row-1">
        <GameLi class="row-one" @liClick="handleOuterClick(0)" v-bind:state="gameOver" v-bind:text="checkText"/>
        <GameLi class="row-one" @liClick="handleOuterClick(1)" v-bind:state="gameOver" v-bind:text="checkText"/>
        <GameLi class="row-one" @liClick="handleOuterClick(2)" v-bind:state="gameOver" v-bind:text="checkText"/>
      </section>
      <section class="row row-2">
        <GameLi class="row-one" @liClick="handleOuterClick(3)" v-bind:state="gameOver" v-bind:text="checkText"/>
        <GameLi class="row-one" @liClick="handleOuterClick(4)" v-bind:state="gameOver" v-bind:text="checkText"/>
        <GameLi class="row-one" @liClick="handleOuterClick(5)" v-bind:state="gameOver" v-bind:text="checkText"/>
      </section>
      <section class="row row-3">
        <GameLi class="row-one" @liClick="handleOuterClick(6)" v-bind:state="gameOver" v-bind:text="checkText"/>
        <GameLi class="row-one" @liClick="handleOuterClick(7)" v-bind:state="gameOver" v-bind:text="checkText"/>
        <GameLi class="row-one" @liClick="handleOuterClick(8)" v-bind:state="gameOver" v-bind:text="checkText"/>
      </section>
    </section>
    <section class="game-result">{{gameOver?'游戏结束':''}}</section>
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
    handleResetClick(){
      this.gameOver = false
    },
    handleOuterClick (index) {
      this.count++
      if(this.gameOver){return}
      if (this.count >= 5) {
        this.checkRules()
        if (this.gameOver) {
          return
        }
      }
      //NOTE:  如果填满了格子,还没有分出胜负也进行返回
      if (this.count === 9 && !this.gameOver) {
        console.log('!!!!!')
        this.gameOver = true
        return
      }
      console.log('this outer click')
      this.checkText = !this.checkText
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
  margin-top:40px;
}
.row {
  display: flex;
}

.row-1, .row-2{
  border-bottom: 5px solid rgb(72, 158, 146);
}
.row-1 >.row-one:nth-child(1){
  border-top-left-radius: 15px;
  border-right: 5px solid rgb(72, 158, 146);
}
.row-1 >.row-one:nth-child(3){
  border-top-right-radius: 15px;
  border-left: 5px solid rgb(72, 158, 146);
}
.row-2 >.row-one:nth-child(1){
  border-right: 5px solid rgb(72, 158, 146);
}
.row-2 >.row-one:nth-child(3){
  border-left: 5px solid rgb(72, 158, 146);
}
.row-3 >.row-one:nth-child(1){
  border-bottom-left-radius: 15px;
  border-right: 5px solid rgb(72, 158, 146);
}
.row-3 >.row-one:nth-child(3){
  border-bottom-right-radius: 15px;
  border-left: 5px solid rgb(72, 158, 146);
}
.reset {
  font-size: 12px;
  padding: 0 20px;
  height: 30px;
  line-height: 30px;
  border-radius: 10px;
  user-select: none;
  cursor: pointer;
  margin-top: 10px;
  outline:none;
}
.reset:hover {
  opacity: .8;
  box-shadow: 0px 2px 10px 2px #c9bbbb;
  transition: all .8s;
}
.game-result {
  margin-top: 20px;
}
</style>
