<template>
    <div class="player">
        <h1>{{ title }}</h1>
    </div>
</template>

<script>
export default {
    name: 'Player',
    props:['title', 'score'],
    data(){
        return {

        }
    }
}
</script>

<style scoped>

</style>
