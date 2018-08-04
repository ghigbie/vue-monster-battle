<template>
  <div class="scoreboard row flex">
      <Player class="card player"
              :name="player1.name" 
              :score="player1.score"/>
      <Player class="card player"
              :name="player2.name" 
              :score="player2.score"/>
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
  .scoreboard{
    margin-top: 10vh;
  }
  .flex {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }
  .player {
    width: 45%;
    text-align: center;
  }
</style>
