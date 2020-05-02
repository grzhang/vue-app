<template>
    <div class="Listdemo-item" :class="{'is-complete':lis.completed}">
        <p>
            <input title="checkbox" type="checkbox" @change="markComplete"/>
            {{lis.title}}
            <button class="del" @click="$emit('deleteItem',lis.id)">x</button>
        </p>
    </div>
</template>

<script>
    export default {
        name: "ListdemoItem",
        props:["lis"],
        methods:{
            markComplete(){
                this.lis.completed = !this.lis.completed;
            }
        }
    }
</script>

<style scoped>
.Listdemo-item{
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #CCC dotted;
}
.is-complete{
    text-decoration: line-through;
}

.del{
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
}
</style>