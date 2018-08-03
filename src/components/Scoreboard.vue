<template>
  <div class="scoreboard">
      <h1>Scoreboard</h1>
      <Player />
      <Player />
  </div>
</template>

<script>
import Player from './Player'

export default {
  name: 'Scoreboard',
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
