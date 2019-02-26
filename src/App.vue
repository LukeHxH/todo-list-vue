<template>
  <div id="app">
    <div class="container mt-3">
      <div class="card">
        <div class="card-header">
          <h1 class="text-center">{{ title }}</h1>
        </div>

        <div class="card-body">
          <TodoList></TodoList>
        </div>

        <div class="card-footer">
          Feito por <a href="https://github.com/LukeHxH" target="_blank">Lucas de Medeiros</a>
        </div>
      </div>
    </div>
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
