<template>
  <div class="app">
    <Header :title="title" />
    <div class="container">
      <Scoreboard :player1="player1"  :player2="player2"/>
      <GameConsole :newGame="newGame" />
    </div>
  </div>

</template>

<script>
import Header from '@/components/Header'
import Scoreboard from '@/components/Scoreboard'
import GameConsole from '@/components/GameConsole'

export default {
  name: 'app',
  components: {
    Header,
    Scoreboard,
    GameConsole
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
  }
}
</script>

<style scoped>

</style>
