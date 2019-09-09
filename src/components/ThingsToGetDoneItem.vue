<template>
    <div class="thingsToDo-item" v-bind:class="{'is-complete':todo.completed}">
        <p>
        <input type="checkbox" v-on:change="markComplete"/>
        {{todo.title}}
        <button @click="$emit('delete-todo', todo.id)" class="delete-button">x</button>
        </p>
    </div>
</template>

<script>
export default {
    name:"ThingsToGetDoneItem",
    props: ["todo"],
    methods:{
        markComplete(){
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>
    .thingsToDo-item{
        background: #ffffff;
        padding: 10px;
        border-bottom: 1px #cccccc dotted;
    }

    .is-complete{
        text-decoration: line-through;
    }
    
    .delete-button{
        background: #D33F49;
        color: #ffffff;
        border: none;
        border-radius:2px;
        float:right;
    }

    .delete-button:hover{
        background:rgb(182, 54, 62);
    }
</style>