<template>
  <div class="app">
    <Scoreboard :player1="player1"  :player2="player2"/>
    <GameConsole />
  </div>

</template>

<script>
import Scoreboard from '@/components/Scoreboard'
import GameConsole from '@/components/GameConsole'

export default {
  name: 'app',
  components: {
    Scoreboard,
    GameConsole
  },
  data(){
    return {
      player1: {
        name: 'You',
        score: 0
      },
      player2: {
        name: 'Monster',
        score: 0
      },
      scoreOverall: 0
    }
  }
}
</script>

<style scoped>

</style>
