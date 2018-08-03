<template>
  <div class="app">
    <Scoreboard />
    <GameConsole />
  </div>

</template>

<script>
import Scoreboard from '@/components/Scoreboard'
import GameConsole from '@/components/GameConsole'

export default {
  name: 'app',
  components: {
    HelloWorld
  }
}
</script>

<style scoped>

</style>
