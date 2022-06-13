<template>
    <div class="todo-app w-75 mx-auto">
        <header class="mb-5">
            <nav class="navbar navbar-dark bg-primary">
                <div class="container-fluid">
                    <h1>
                        <a class="navbar-brand" href="#">Todo Application v1.0</a>
                    </h1>
                </div>
            </nav>
        </header>
   
        
        <div class="mx-auto">
            <div class="d-flex justify-content-between mb-3">
                <input type="text" name="" id="" class="form-control w-75" v-model="text">
                <button v-on:click="Submit" class="btn btn-primary d-block px-4">Add</button>
            </div>

            <table class="table">
                <thead>
                    <tr>
                        <th>Task</th>
                        <th>Author</th>
                        <th>Delete</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="item in items" v-bind:key="item.id">
                        <td class="h2">{{ item.title }}</td>
                        <td class="h2">Gonzales54</td>
                        <td><button v-on:click="Delete(item)" class="btn btn-danger">Delete</button></td>
                    </tr>
                </tbody>
            </table>
        </div>

        


    </div>
</template>

<script>
export default{
    name: 'MainTodo2',
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
                if(this.items.length == 0){
                    this.items.push(
                        {'id': 1, 'title': this.text}   
                    )
                    localStorage.setItem('items', JSON.stringify(this.items))
                    this.text = ''
                }else{
                    this.items.push(
                        {'id': this.items.length + 1, 'title': this.text}   
                    )
                    localStorage.setItem('items', JSON.stringify(this.items))
                    this.text = ''
                }
            }
        },
        Delete: function(num){
            let index = this.items.indexOf(num);
            this.items.splice(index, 1);
            localStorage.setItem('items', JSON.stringify(this.items))
        }
    }
}
</script>

<style></style>
