<template>
    <div class="player center-text">
        <h1>{{ name }}</h1>
        <h2>{{ health }}</h2>
        <div class="healthbar-outer">
            <div class="healthbar"
                :style="{width: health + '%'}">
                <h3 class="inner-text">{{ health }}</h3>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Player',
    props:['name', 'health'],
    data(){
        return {

        }
    }
}
</script>

<style scoped>
    .healthbar-outer{
        background-color: rgb(72, 83, 83);
        width: 95%;
        margin: 1vh auto;
        text-align: center;
    }
    .healthbar{
        background-color: green;
        margin: 0;
        color: #fff;
        height: 5vh;
        width: 100%;
        text-align: center;
    }
    .inner-text{
        position: absolute;
        left: 47.5%;
    }
</style>
