<template>
    <div class="data-console card">
        <ul>
            <li v-for="(turn, index) in turns" key="index">
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
    li{
        list-style-type: none;
        font-weight: 800;
    }

</style>

