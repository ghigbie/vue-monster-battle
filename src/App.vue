<template>
  <div class="app">
    <Header :title="title" />
    <div class="container">
      <Scoreboard :player1="player1"  
                  :player2="player2"/>
      <GameConsole :newGame="newGame"
                   :turns="turns"
                   @startGame="onStartGame" 
                   @attack="onAttack"
                   @specialAttack="onSpecialAttack"
                   @heal="onHeal"
                   @retreat="onRetreat"/>
    </div>
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
      gameHealth: 100,
      turns: []
    }
  },
  methods: {
    onStartGame(){
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
          this.onEndGame();
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
      this.turns = [];
      this.newGame = !this.newGame;
    },
    //game control methods
    calculateDamange(min, max){
      return Math.max(Math.floor(Math.random() * max) +1, min);
    },
    onAttack(){
      let damage = this.calculateDamange(3, 10)
      this.player2.health -= damage;
      this.turns.unshift({
        isPlayer1: true,
        text: `You dealt ${damage} points of damange to ${this.player2.name}`
      })
      if(this.checkWin()){
        return;
      }
      this.player2Attacks();
    },
    onSpecialAttack(){
      let damage = this.calculateDamange(10, 20);
      this.player2.health -= damage;
      this.turns.unshift({
        isPlayer1: true,
        text: `Excellent move! ${this.player1.name} dealt ${damage} points of damange to ${this.player2.name}.`
      });
      if(this.checkWin()){
        return;
      }
      this.player2Attacks();
    },
    onHeal(){
      if(this.player1.health < this.gameHealth){
        let increase = Math.floor(Math.random() * 10) +1;
        this.player1.health += increase
        this.turns.unshift({
          isPlayer1: true,
          text: `You healed by ${increase} points.`
      });
      }
        if(this.player1.health > this.gameHealth){
          this.player1.health = this.gameHealth;
      }
      this.monsterAttacks();
    },
    onRetreat(){
      confirm('Are you sure you want to run away?');
      alert('You lost!');
      this.onEndGame();
    },
    player2Attacks(){
      let damage = this.calculateDamange(5, 12);
      this.player1.health -= damage;
      this.turns.unshift({
        isPlayer1: false,
        text: `${this.player2.name} dealt ${damage} points of damange to ${this.player1.name.toLowerCase()}.`
      });
      this.checkWin();
    }
  }
}
</script>

<style scoped>

</style>
