<template>
    <div class="player">
        <h1>{{ name }}</h1>
        <h2>{{ score }}</h2>
    </div>
</template>

<script>
export default {
    name: 'Player',
    props:['name', 'score'],
    data(){
        return {

        }
    }
}
</script>

<style scoped>

</style>
