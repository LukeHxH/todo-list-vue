<template>
    <b-list-group-item class="mb-2 d-flex justify-content-between">
        <div class="todo-item-right">
            <div v-if="!item.editing" class="todo-item-label"
            @dblclick="edit(item)">
                {{ item.description }}
            </div>
            
            <b-form-input v-else class="todo-item-edit"
            v-model="item.description" @keyup.enter="doneEdit(item)"
            @keyup.esc="cancelEdit(item)" @blur="doneEdit(item)" v-focus>
            </b-form-input>
        </div>

        <div>
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
    .todo-item-edit {
        font-size: 24px;
        color: #2c3e58;
    }
</style>
