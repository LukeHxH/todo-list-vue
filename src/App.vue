<template>
  <div id="app">
    <b-container>
      <h1 class="text-center mb-3">{{title}}</h1>

      <b-input-group append="Adicionar item" class="mb-2">
        <b-form-input v-model="content" @keyup.enter="addItem()" autofocus>

        </b-form-input>
      </b-input-group>

      <b-list-group v-for="(item, index) in todoList" :key="index">
          <b-list-group-item class="mb-2">

            <TodoItem :item="item" @remove="removeItem(index)">
              Item {{item.index + 1}}
            </TodoItem>

          </b-list-group-item>
      </b-list-group>
    </b-container>
  </div> 
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
  name: 'app',
  data () {
    return {
      title: 'Lista de afazeres',
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
