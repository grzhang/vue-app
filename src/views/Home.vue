<template>
  <div id="app">
    <AddTodo v-on:handleAdd="handleAdd"></AddTodo>
    <List :list="todos" @handleDelete="handleDelete"></List>
  </div>
</template>

<script>
    import List from "../components/List";
    import AddTodo from "../components/AddTodo";
    import axios from "axios"
    export default {
        name:"Home",
        data(){
            return{
                msg:"hello",
                todos:[]
            };
        },
        components:{
            List,
            AddTodo
        },
        methods:{
            handleDelete(id){
                axios.delete(`http://jsonplaceholder.typicode.com/todos/${id}`).then(
                    res => this.todos = this.todos.filter(todo => todo.id !== id)
                )

            },
            handleAdd(newTodo){
                const {title,completed} = newTodo;
                axios
                    .post("http://jsonplaceholder.typicode.com/todos",{
                        title,
                        completed
                    })
                    .then(res => this.todos.unshift(res.data))
                    .catch(err => console.log(err));

            }
        },
        created(){
            axios
                .get('http://jsonplaceholder.typicode.com/todos?_limit=10')
                .then(res => this.todos = res.data)
                .catch(function (error) {
                    console.log(error);
                })
        }
    }
</script>

<style>
  *{
    box-sizing: border-box;
    margin: 0;
  }

  body{
    line-height: 1.4;
  }

  .btn{
    display: inline-block;
    border:none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover{
    background: #666;
  }
</style>
