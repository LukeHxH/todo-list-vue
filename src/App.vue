<template>
  <div id="app">
    <h1 class="text-center mt-3">{{ title }}</h1>
    <TodoList></TodoList>
  </div> 
</template>

<script>
import TodoList from './TodoList.vue';

export default {
  name: 'app',
  data () {
    return {
      title: 'Lista de afazeres com Vue.js'
    }
  },
  components: { TodoList }
}
</script>
