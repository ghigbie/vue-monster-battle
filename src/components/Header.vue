<template>
    <div class="header">
        <nav class="navbar navbar-dark bg-dark">
            <div class="inner-container container">
                <h1 class="page-title">{{ title }}</h1>
            </div>
        </nav>
    </div>
</template>

<script>

export default {
    name: 'Header',
    props: ['title'],
    data(){
        return {

        }
    }
}
</script>

<style scoped>
    .inner-container {
        display: flex;
        flex-direction: row;
        justify-content: center;
    }
    .page-title{
        position: relative;
        padding: 2vh;
        color: #e8e8e8;
        transform: translateX(-50%); 
    }
</style>
