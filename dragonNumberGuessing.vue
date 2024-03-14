<template>  
  <div id="app">  
    <h1>猜数字游戏</h1>  
    <p v-if="gameStatus === 'playing'">已经生成了一个1到10之间的数字，您有四次机会来猜它。</p>  
    <p v-else-if="gameStatus === 'won'">恭喜您，您猜对了！</p>  
    <p v-else-if="gameStatus === 'lost'">很遗憾，您没有在四次机会内猜中数字。</p>  
    <input v-model.number="userGuess" type="number" min="1" max="10" v-if="gameStatus === 'playing'" @keyup.enter="checkGuess" />  
    <button v-if="gameStatus === 'playing'" @click="checkGuess">猜</button>  
    <button v-else @click="startGame">重新开始</button>  
    <p>当前猜测次数: {{ guessCount }}</p>  
  </div>  
</template>  
  
<script>  
export default {  
  data() {  
    return {  
      randomNumber: null,  
      userGuess: null,  
      guessCount: 0,  
      guessLimit: 4,  
      gameStatus: 'notStarted',  
    };  
  },  
  methods: {  
    startGame() {  
      this.randomNumber = Math.floor(Math.random() * 10) + 1;  
      this.guessCount = 0;  
      this.gameStatus = 'playing';  
      this.userGuess = null;  
    },  
    checkGuess() {  
      if (this.guessCount >= this.guessLimit) {  
        this.gameStatus = 'lost';  
        alert('很遗憾，您没有在四次机会内猜中数字。');  
        return;  
      }  
      if (this.userGuess === this.randomNumber) {  
        this.gameStatus = 'won';  
        alert('恭喜您，您猜对了！');  
      } else if (this.userGuess < this.randomNumber) {  
        alert('猜的数字太小了，请再试一次。');  
      } else {  
        alert('猜的数字太大了，请再试一次。');  
      }  
      this.guessCount++;  
      this.userGuess = null; // 重置输入框值  
    },  
  },  
  created() {  
    this.startGame();  
  },  
};  
</script>  
  
<style>  
/* css */  
</style>