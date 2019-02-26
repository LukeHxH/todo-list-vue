<template>
  <div id="app">
    <h1 class="text-center">{{ title }}</h1>
    <TodoList></TodoList>
  </div> 
</template>

<script>
import TodoList from './TodoList.vue';

export default {
  name: 'app',
  data () {
    return {
      title: 'Todo List with Vue.js'
    }
  },
  components: { TodoList }
}
</script>

<style>
  #app {
    font-size: 24px;
  }
</style>
