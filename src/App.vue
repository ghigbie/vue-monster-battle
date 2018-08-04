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
    }
  },
  methods: {
    onStartGame(){
      console.log("upper component start game called");
      this.newGame = !this.newGame;
      this.player1.score = 100;
      this.player2.score = 100;

    }
  }
}
</script>

<style scoped>

</style>
