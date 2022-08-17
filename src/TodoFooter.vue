<template>
   <footer class="footer">
     <span class="todo-count">
       <span>{{todoNum}}</span>
       <span v-if="todoNum<=1"> item left</span>
       <span v-else> items left</span>
     </span>
     <ul class="filters">
       <li><a href="#/all" class="selected">All</a></li>
       <li><a href="#/active">Active</a></li>
       <li><a href="#/completed">Completed</a></li>
     </ul>
     <button class="clear-completed">Clear Completed</button>
   </footer>
</template>

<script>
export default {
  name: "TodoFooter",
  data(){
    return{

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