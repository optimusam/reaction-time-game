<template>
  <div class="container is-center">
  <h1 class="title">Reaction Time Game</h1>
  <button class="button is-primary" :disabled="isPlayBtnDisabled" @click="startGame">Play</button>
  <Block :show="showBlock"  @gameover="endGame"/>
  <Result :show="showResult" :reactionTime="reactionTime"/>
  </div>
</template>

<script>
  import Block from './components/Block.vue'
  import Result from './components/Result.vue'

  export default {
    components: { Block, Result },

    data() {
      return {
        showBlock: false,
        showResult: false,
        isPlayBtnDisabled: false,
        reactionTime: null
      }
    },

    methods: {
      startGame() {
        this.showBlock = false;
        this.showResult = false;
        this.isPlayBtnDisabled = true;
        const pause = this.randomIntFromInterval(1,3);
        setTimeout(() => this.showBlock = true, pause*1000);
      },

      endGame(reactionTime) {
        this.reactionTime = reactionTime;
        this.showBlock = false;
        this.showResult = true;
        this.isPlayBtnDisabled = false;
      },

      randomIntFromInterval(min, max) { // min and max included 
        return Math.floor(Math.random() * (max - min + 1) + min)
      }
    }

  }
</script>

<style>
  .container {
    margin: 0 25%;
  }
</style>
