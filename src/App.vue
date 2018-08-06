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
      this.newGame = true;
      this.player1.health = this.gameHealth;
      this.player2.health = this.gameHealth;
    },
    checkWin(){
      if(this.player2.health <= 0){
        if(confirm('You won! New Game?')){
          this.onStartGame()
        }else{
          this.player2.health = 0;
          this.onEndGame
        }
        return true;
      }else if(this.player1.health <= 0){
        if(confirm('Monster won! New Game?')){
          this.onStartGame();
        }else{
          this.player1.health = 0;
          this.onEndGame();
        }
        return true;
      }
      return false;
    },
    onEndGame(){
      this.newGame = !this.newGame;
    },
    //game control methods
    calculateDamange(min, max){
      return Math.max(Math.floor(Math.random() * max) +1, min);
    },
    onAttack(){
      this.player2.health -= this.calculateDamange(3, 10)
      if(this.checkWin()){
        return;
      }
      this.player2Attacks();
    },
    onSpecialAttack(){
      this.player2.health -= this.calculateDamange(10, 20)
      if(this.checkWin()){
        return;
      }
      this.player2Attacks();
    },
    onHeal(){
      if(this.player1.health < this.gameHealth){
        this.player1.health += Math.floor(Math.random() * 10) +1;
      }
        if(this.player1.health > this.gameHealth){
          this.player1.health = this.gameHealth;
      }
      this.monsterAttacks();
    },
    onGiveUp(){
      confirm('Are you sure you want to run away?');
      alert('You lost!');
      this.onEndGame();
    },
    player2Attacks(){
      this.player1.health -= this.calculateDamange(5, 12);
      this.checkWin();
    }
  }
}
</script>

<style scoped>

</style>
