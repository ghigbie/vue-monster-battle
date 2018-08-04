<template>
    <div class="game-console card">
        <h1>Game Console</h1>
        <div class="button-holder">
            <template v-if="newGame">
                <button class="btn btn-success"
                        @click="startGame">Start</button>
            </template>
            <template v-else>
                <button class="btn btn-warning controls">Attack</button>
                <button class="btn btn-danger controls">Special Attack</button>
                <button class="btn btn-primary controls">Heal</button>
                <button class="btn btn-dark controls">Give Up</button>
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
            this.$emit('startGame');
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
    .controls{
        margin: 3px;
    }
</style>
