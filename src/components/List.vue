<template>
    <div id="List">
        <div :key="index" v-for="(lis,index) in list">
            <Lisitem :lis="lis" @deleteItem="$emit('handleDelete',lis.id)"></Lisitem>
        </div>
    </div>
</template>

<script>
    import Lisitem from "./ListdemoItem"
    export default {
        name: "List",
       // props:["list"]
        props:{
            list:{
                type:Array
            }
        },
        components:{
            Lisitem
        }
    }
</script>

<style scoped>

</style>