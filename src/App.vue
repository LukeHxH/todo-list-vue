<template>
  <div id="app">
    <h1>{{title}}</h1>
    
    <input type="text" placeholder="Digite um item para adicionar na lista..."
    v-model="content" @keyup.enter="addItem()" autofocus>

    <ul v-for="(item, index) in todoList" :key="index">
      <li>
        <TodoItem :item="item" @remove="removeItem(index)">
          Item {{item.index + 1}}
        </TodoItem>
      </li>
    </ul>
  </div> 
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
  name: 'app',
  data () {
    return {
      title: 'Lista de afazeres (to-do list)',
      content: '',
      todoList: []
    }
  },
  components: { TodoItem },
  methods: {
    addItem() {
      this.todoList.push({'description': this.content});
      this.content = '';
    },
    removeItem(index) {
      this.todoList.splice(index, 1);
    }
  }
}
</script>
