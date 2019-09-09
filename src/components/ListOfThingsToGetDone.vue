<template>
    <div>
        <div v-bind:key="todo.id" v-for="todo in thingsToGetDone">
            <ThingsToGetDoneItem v-bind:todo="todo" v-on:delete-todo="$emit('delete-todo', todo.id)"/>
        </div>
    </div>
</template>

<script>
import ThingsToGetDoneItem from './ThingsToGetDoneItem'

export default {
    name: 'ListOfThingsToGetDone',
    components:{
        ThingsToGetDoneItem
    },
    props: ['thingsToGetDone']
}
</script>

<style scoped>

</style>