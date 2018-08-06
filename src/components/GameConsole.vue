<template>
    <div>
    <div class="game-console card">
        <h1>Game Console</h1>
        <div class="button-holder">
            <section v-if="!newGame">
                <button class="btn btn-success"
                        @click="startGame">Start</button>
            </section>
            <section v-else>
                <button class="btn btn-warning controls"
                        @click="attack">Attack</button>
                <button class="btn btn-danger controls"
                        @click="specialAttack">Special Attack</button>
                <button class="btn btn-primary controls"
                        @click="heal">Heal</button>
                <button class="btn btn-dark controls"
                        @click="retreat">Retreat</button>
            </section>
        </div>
    </div>
        <DataConsole class="data-console"
                     v-if="turns.length"
                     :turns="turns"/>
    </div>
</template>

<script>
import DataConsole from './DataConsole';

export default {
    name: 'GameConsole',
    props: ['newGame', 'turns'],
    components: {
        DataConsole
    },
    data(){
        return {
        }
    },
    methods: {
        startGame(){
            this.$emit('startGame');
        },
        attack(){
            this.$emit('attack');
        },
        specialAttack(){
            this.$emit('specialAttack');
        },
        heal(){
            this.$emit('heal');
        },
        retreat(){
            this.$emit('retreat');
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
    .data-console{
        margin: 2vh 0;
        text-align: center;
        padding: 5px;
    }
</style>
