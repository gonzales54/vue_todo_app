<template>
    <div class="todo">
        <h1 class="text-center">Hello World</h1>
        
        <div class="mx-auto w-50 mb-5">
            <input type="text" name="" id="" class="form-control mb-4" v-model="text">
            <div class="d-flex">
                <button v-on:click="Submit" class="btn btn-primary mx-auto d-block">Add</button>
                <button v-on:click="Delete" class="btn btn-danger mx-auto d-block">Delete</button>
            </div>
        </div>

        <ul class="mx-auto w-50 list-group">
            <li class="list-group-item" v-for="item in items" v-bind:key="item.id">{{item.title}}</li>
        </ul>
    </div>
</template>

<script>

export default{
    name: 'MainTodo1',
    data(){
        return{
            text: '',
            items: [],
        }
    },
    
    mounted: function(){
        this.items = JSON.parse(localStorage.getItem('items'))
        return(this.items);
    },

    methods: {
        Submit: function(){
            if(this.text != ''){
                this.items.push(
                    {'id': (this.items.length + 1), 'title': this.text}   
                )
                localStorage.setItem('items', JSON.stringify(this.items))
                this.text = ''
            }
        },
        Delete: function(){
            this.items = this.items.slice(1, this.items.length);
            localStorage.setItem('items', JSON.stringify(this.items))
        }
    }
}
</script>

<style></style>
