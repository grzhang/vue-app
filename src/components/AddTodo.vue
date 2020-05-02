<template>
    <div>
        <form @submit.prevent="addTodo">
            <input v-model="title" type="text" name="title" placeholder="请添加待办事项。。。"/>
            <input type="submit" value="添加" class="btn"/>
        </form>
    </div>
</template>

<script>
   // import { v4 as uuidv4 } from 'uuid';
    export default {
        name: "AddTodo",
        data(){
            return{
                title:""
            }
        },
        methods:{
            addTodo(){
                const newTodo = {
                    //id:uuidv4(),
                    title:this.title,
                    completed:false
                }
                this.$emit("handleAdd",newTodo);
                this.title = "";
            }
        }
    }
</script>

<style scoped>
form{
    display: flex;
}

input[type = "text"]{
    flex: 10;
    padding: 5px;
}

input[type = "submit"]{
    flex: 2;
}
</style>