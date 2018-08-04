<template>
  <div class="scoreboard">
      <h1>Scoreboard</h1>
      <Player name="player1.name" score="player1.score"/>
      <Player name="player2.name" score="player2.score"/>
  </div>
</template>

<script>
import Player from './Player'

export default {
  name: 'Scoreboard',
  props: ['player1', 'player2'],
  components: {
    Player
  },
  data(){
    return {
      
    }
  }
}
</script>

<style scoped>

</style>
