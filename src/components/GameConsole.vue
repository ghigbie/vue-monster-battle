<template>
    <div class="game-console card">
        <h1>Game Console</h1>
        <div class="button-holder">
            <template v-if="newGame">
                <button class="btn btn-success"
                        @click="startGame">Start</button>
            </template>
            <template v-else>
                <button class="btn btn-warning">Attack</button>
                <button class="btn btn-danger">Special Attack</button>
                <button class="btn btn-primary">Heal</button>
                <button class="btn btn-dark">Give Up</button>
            </template>
        </div>
    </div>
</template>

<script>
export default {
    name: 'GameConsole',
    props: ['newGame'],
    data(){
        return {
        }
    },
    methods: {
        startGame(){
            console.log('start game called');
        }
    }
}
</script>

<style scoped>
    .game-console{
        text-align: center;
        margin-top: 7vh;
        padding: 25px;
    }
</style>
