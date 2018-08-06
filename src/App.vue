<template>
  <div class="app">
    <Header :title="title" />
    <div class="container">
      <Scoreboard :player1="player1"  
                  :player2="player2"/>
      <GameConsole :newGame="newGame"
                   @startGame="onStartGame" 
                   @attack="onAttack"
                   @specialAttack="onSpecialAttack"
                   @heal="onHeal"
                   @giveUp="onGiveUp"/>
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
        health: 0
      },
      player2: {
        name: 'Monster',
        health: 0
      },
      scoreOverall: 0,
      newGame: false,
      gameHealth: 100
    }
  },
  methods: {
    onStartGame(){
      console.log("upper component start game called");
      this.newGame = !this.newGame;
      this.player1.health = this.gameHealth;
      this.player2.health = this.gameHealth;
    },
    checkScore(){
      this.player1.health <= this.gameHealth && this.onEndGame();
      this.player2.health <= this.gameHealth && this.onEndGame();
    },
    onEndGame(){
      this.newGame = !this.newGame;
      console.log('On end Game called');
    },
    //game control methods
    onAttack(){
      let max = 10;
      let min = 3;
      let damage = Math.max(Math.floor(Math.random() * max) +1, min);
      this.player1.health -= damage;

      max = 12;
      min = 5;
      damage = Math.max(Math.floor(Math.random() * max) + 1, min);
      this.player2.health -= damage;
    },
    onSpecialAttack(){

    },
    onHeal(){

    },
    onGiveUp(){

    }
  }
}
</script>

<style scoped>

</style>
