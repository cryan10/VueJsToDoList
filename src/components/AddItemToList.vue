<template>
    <div>
        <form @submit="addItem">
            <input type="text" v-model="title" name="title" placeholder="Add item">
            <input type="submit" value="Add" class="button">
        </form>
    </div>
</template>

<script>
export default {
    name: "AddItemToList",
    data(){
        return{
            title: ''
        }
    },
    methods:{
        addItem(e){
            e.preventDefault();
            const newItem = {
                title: this.title,
                completed: false
            }
            this.$emit('add-item', newItem);
            this.title = '';
        }
    }
}
</script>

<style scoped>
    form{
        display:flex;
    }

    input[type='text']{
        flex: 10;
        padding: 5px; 
    }

    input[type='submit']{
        flex: 2;
    }
</style>