<template>
    <b-list-group-item class="mb-2 d-flex justify-content-between">
        <div class="todo-item-right">
            <div v-show="!item.editing" class="todo-item-label"
            @dblclick="edit(item)">
                {{ item.description }}
            </div>
            
            <b-form-input v-show="item.editing" class="todo-item-edit"
            v-model="item.description" @keyup.enter="doneEdit(item)">
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
    methods: {
        edit(item) {
            item.editing = true;
        },
        
        doneEdit(item) {
            if (item.description.trim().length > 0) {
                item.editing = false;
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
