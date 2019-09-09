<template>
  <div id="app">
    <Header />
    <AddItemToList v-on:add-item="addItem" />
    <ListOfThingsToGetDone v-bind:thingsToGetDone="thingsToGetDone" v-on:delete-todo="deleteItem"/>
  </div>
</template>

<script>
import Header from './components/layout/header';
import ListOfThingsToGetDone from './components/ListOfThingsToGetDone';
import AddItemToList from './components/AddItemToList';
import axios from 'axios';

export default {
  name: 'app',
  components: {
    Header,
    AddItemToList,
    ListOfThingsToGetDone
  },
  data(){
    return {
      thingsToGetDone:[]
    }
  },
  methods: {
    deleteItem(id){
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(this.thingsToGetDone = this.thingsToGetDone.filter(thingToGetDone => thingToGetDone.id !== id))
      .catch(error => console.log(error));
    },
    addItem(newItem){
      const {title, completed} = newItem;
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title, 
        completed})
        .then(response => this.thingsToGetDone = [...this.thingsToGetDone, newItem])
        .catch(error => console.log(error));
    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=8&completed=false')
    .then(res => this.thingsToGetDone = res.data)
    .catch(error => console.log(error));
  }
}
</script>

<style>
#app {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
  color:#262730;
}

.button{
  display:inline-block;
  border:none;
  background: #77BA99;
  color: #ffffff;
  padding: 7px 20px;
  cursor:pointer;
}

.button:hover{
  background:rgb(98, 151, 124);
}
</style>
