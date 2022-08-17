<template>
   <li :class="{completed:todo.hasCompleted,editing:editedTodo==todo}">
     <div class="view">
       <input type="checkbox" class="toggle"  v-model="check">
       <label @dblclick="editTodo">{{todo.value}}</label>
       <button class="destroy" @click="delTodo"></button>
     </div>
     <input type="text" class="edit" :value="todo.value" v-focus @keyup.enter="doneTodo" @blur="doneTodo" @keyup.esc="cancelTodo" >
   </li>
</template>


<script>
    export default {
        name:"TodoItem",
        props:['todo'],
        data(){
            return{
                editedTodo:""
            }
        },
        methods: {
            delTodo(){
                this.$parent.todoDatas=this.$parent.todoDatas.filter(value=>{
                    return !(value.id==this.todo.id)
                })
            },
            editTodo(){
                this.editedTodo=this.todo;
            },
            doneTodo(e){
                this.$parent.todoDatas=this.$parent.todoDatas.map(v=>{
                    if(v.id==this.todo.id){
                        v.value=e.target.value.trim();
                    }
                    return v;
                })
                this.editedTodo=''
            },
            cancelTodo(){
                this.editedTodo=''
            }

        },
        computed:{
            check:{
                get(){
                    console.log("get")
                    return this.todo.hasCompleted
                },
                set(value){  
                    this.$parent.todoDatas=this.$parent.todoDatas.map(v=>{
                        if(v.id==this.todo.id){
                            v.hasCompleted=value;
                        }
                        return v
                    })
                }
            }
        },
        directives:{
            focus(elm){
                elm.focus()
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>