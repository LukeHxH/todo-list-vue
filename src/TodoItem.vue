<template>
    <b-list-group-item class="mb-2 d-flex bd-highlight" id="item">
        <div class="bd-highlight p-2">
            <b-form-checkbox v-model="item.completed"/>
        </div>

        <div class="bd-highlight ml-2">
            <div v-if="!item.editing" @dblclick="edit(item)"
            class="todo-item-label" :class="{completed : item.completed}">
                <span>{{ item.description }}</span>
            </div>
            
            <b-form-input v-else class="todo-item-edit"
            v-model="item.description" @keyup.enter="doneEdit(item)"
            @keyup.esc="cancelEdit(item)" @blur="doneEdit(item)" v-focus>
            </b-form-input>
        </div>

        <div class="bd-highlight ml-auto">
            <b-button variant="danger" @click="$emit('remove')">
                Excluir
            </b-button>
        </div>
    </b-list-group-item>
</template>

<script>
export default {
    name: 'TodoItem',
    
    props: {
        item: Object
    },

    data () {
        return {
            beforeEditCache: ''
        }
    },

    methods: {
        edit(item) {
            this.beforeEditCache = item.description
            item.editing = true
        },

        doneEdit(item) {
            if (item.description.trim().length === 0) {
                item.description = this.beforeEditCache
            }

            item.editing = false
        },

        cancelEdit(item) {
            item.editing = false
            item.description = this.beforeEditCache
            this.beforeEditCache = ''
        }
    },

    directives: {
        focus: {
            inserted: (el) => {
                el.focus()
            }
        }
    }
}
</script>


<style>
    #item {
        font-size: 24px;
    }

    .todo-item-edit {
        font-size: 24px;
        color: #2c3e58;
    }

    .completed {
        text-decoration: line-through;
        color: grey;
    }
</style>
