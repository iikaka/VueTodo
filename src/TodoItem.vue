<template>
   <li>
     <div class="view">
       <input type="checkbox" class="toggle">
       <label>{{todo.value}}</label>
       <button class="destroy" @click="delTodo"></button>
     </div>
     <input type="text" class="edit">
   </li>
</template>


<script>
    export default {
        name:"TodoItem",
        props:['todo'],
        methods: {
            delTodo(){
                this.$parent.todoDatas=this.$parent.todoDatas.filter(value=>{
                    return !(value.id==this.todo.id)
                })
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>