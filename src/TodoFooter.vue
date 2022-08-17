<template>
   <footer class="footer">
     <span class="todo-count">
       <span>{{todoNum}}</span>
       <span v-if="todoNum<=1"> item left</span>
       <span v-else> items left</span>
     </span>
     <ul class="filters">
       <li><a href="#/all" @click="filterTodo('all')" :class="{selected:$parent.view=='all'}">All</a></li>
       <li><a href="#/active" @click="filterTodo('active')" :class="{selected:$parent.view=='active'}">Active</a></li>
       <li><a href="#/completed" @click="filterTodo('completed')" :class="{selected:$parent.view=='completed'}"> Completed</a></li>
     </ul>
     <button class="clear-completed">Clear Completed</button>
   </footer>
</template>

<script>
export default {
  name: "TodoFooter",
  methods: {
    filterTodo(value){
        this.$parent.view=value;
    }
  },
  computed:{
    todoNum(){
        return this.$parent.todoDatas.filter(value=>{
            return !value.hasCompleted
        }).length
    }
  }
}
</script>

<style scoped>

</style>