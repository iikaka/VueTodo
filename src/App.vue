<template>
  <section class="todoapp">
    <header class="header">
      <h1>Todos</h1>
      <input type="text" class="new-todo" v-model="newTodo" @keyup.enter="addTodo">
    </header>
    <section class="main">
         <input type="checkbox" id="toggle-all" class="toggle-all" v-model="isAll">
        <label for="toggle-all" ></label>
        <ul class="todo-list">
             <todo-item v-for="todo in todoDatas" :key="todo.id" :todo="todo"></todo-item>
        </ul>
      </section>
     <todo-footer></todo-footer>
  </section>
</template>

<script>
import TodoItem from '@/TodoItem.vue';
import TodoFooter from '@/TodoFooter.vue'
export default {
    name:'App',
    components:{TodoItem,TodoFooter},
    data(){
      return{
        todoDatas:[],
        newTodo:'',
      }
    },
    methods:{
      addTodo(){
        if(this.newTodo=='') return
        let todo={}
        todo.id=Date.now();
        todo.value=this.newTodo.trim();
        todo.hasCompleted=false;
        this.todoDatas.push(todo);
        this.newTodo=''
      }
    },
      computed:{
        isAll:{
          get(){
            return false;
          },
          set(value){
            this.todoDatas.map(todo=>{
              todo.hasCompleted=value;
              return value;
            })
          }
        }
      }

  }
</script>

<style  scoped>

</style>