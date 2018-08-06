<template>
    <div class="data-console card">
        <ul>
            <li v-for="(turn, index) in turns" 
                key="index"
                :class="{ 'player1-turn': turn.isPlayer1 , 'player2-turn': !turn.isPlayer1 }">
                {{ turn.text }}
            </li>
        </ul>
    </div>
</template>


<script>
export default {
    name: 'DataConsole',
    props: ['turns'],
    data(){
        return {

        }
    }
}
</script>

<style scoped>
    .data-console{
        background-color: #212529;
    }
    li{
        list-style-type: none;
        font-weight: 800;
        color: #c7c4c4
    }
    .player1-turn{
        color:#066464;
        background-color: #e4e8ff;
    }
    .player2-turn{
        color: #fa0808;
        background-color: #ffc0c1
    }

</style>

