<template>
  <div class="app">
    <Header :title="title" />
    <div class="container">
      <Scoreboard :player1="player1"  
                  :player2="player2"/>
      <GameConsole :newGame="newGame"
                   @startGame="onStartGame" />
    </div>
    <Footer />
  </div>

</template>

<script>
import Header from '@/components/Header'
import Scoreboard from '@/components/Scoreboard'
import GameConsole from '@/components/GameConsole'
import Footer from '@/components/Footer'

export default {
  name: 'app',
  components: {
    Header,
    Scoreboard,
    GameConsole,
    Footer
  },
  data(){
    return {
      title: 'Monster Battle',
      player1: {
        name: 'You',
        score: 0
      },
      player2: {
        name: 'Monster',
        score: 0
      },
      scoreOverall: 0,
      newGame: true,
      lifeScore: 100
    }
  },
  methods: {
    onStartGame(){
      console.log("upper component start game called");
      this.newGame = !this.newGame;
      this.player1.score = this.lifeScore;
      this.player2.score = this.lifeScore;
    },
    checkScore(){
      this.player1.score <= this.lifeScore && this.onEndGame();
      this.player2.score <= this.lifeScore && this.onEndGame();
    },
    onEndGame(){
      this.newGame = !this.newGame;
      console.log('On end Game called');
    },
  }
}
</script>

<style scoped>

</style>
