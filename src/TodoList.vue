<template>
    <b-container class="p-3 mt-2 bg-light border">
      <b-input-group class="mb-2">
        <b-form-input v-model="newTodo" @keyup.enter="addItem" autofocus
        placeholder="What needs to be done...">
        </b-form-input>
        <b-input-group-append>
          <b-button variant="info" @click="addItem">Adicionar</b-button>
        </b-input-group-append>
      </b-input-group>

        <b-list-group v-for="(item, index) in todos" :key="index">
            <TodoItem :item="item" @remove="removeItem(index)"></TodoItem>
        </b-list-group>
    </b-container>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
    name: 'TodoList',
    data () {
        return {
            newTodo: '',
            newId: 1,
            todos: [],
        }
    },
    components: { TodoItem },
    methods: {
        addItem() {

            if (this.newTodo.trim().length != 0) {
                this.todos.push({
                    id: this.newId++,
                    description: this.newTodo,
                    completed: false,
                    editing: false
                });
            }

            this.newTodo = '';
        },

        removeItem(index) {
            this.todos.splice(index, 1);
        }
    }
}
</script>
