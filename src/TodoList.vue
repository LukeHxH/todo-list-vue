<template>
    <b-container class="p-3 mt-2 bg-light border">
        <b-input-group class="mb-2">
        <b-form-input v-model="newTodo" @keyup.enter="addItem" autofocus
        placeholder="O que eu preciso fazer?">
        </b-form-input>

        <b-input-group-append>
            <b-button variant="info" @click="addItem">Adicionar</b-button>
        </b-input-group-append>
        </b-input-group>

        <p v-if="todos.length == 0" class="text-center font-italic mb-0">
            Nenhuma tarefa a ser feita...
        </p>
        <div v-else>
            <b-list-group class="mt-3 mb-3" v-for="(item, index) in todos" :key="index">
                <TodoItem :item="item" @remove="removeItem(index)"></TodoItem>
            </b-list-group>

            <div class="d-flex justify-content-between">
                <div>
                    <label>
                        <b-form-checkbox :checked="!anyRemaining" @change="checkAllTodos">
                            {{ checkAllText }} todos
                        </b-form-checkbox>
                    </label>
                </div>

                <div>{{ remaining }} tarefas restantes</div>
            </div>
        </div>
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

    computed : {
        remaining() {
            return this.todos.filter(todo => !todo.completed).length
        },

        anyRemaining() {
            return this.remaining > 0
        },

        checkAllText() {
            return this.remaining > 0 ? "Marcar " : "Desmarcar "
        }
    },

    methods: {
        addItem() {

            if (this.newTodo.trim().length != 0) {
                this.todos.push({
                    id: this.newId++,
                    description: this.newTodo,
                    completed: false,
                    editing: false
                })
            }

            this.newTodo = ''
        },

        removeItem(index) {
            this.todos.splice(index, 1)
        },

        checkAllTodos() {
            this.todos.forEach((todo) => todo.completed = event.target.checked);
        }
    }
}
</script>
