<template>
    <div class="container">
        <span>{{ item.description }}</span>
        <button @click="$emit('remove')">remover</button>
    </div>
</template>

<script>
export default {
    props: {
        item: Object
    }
}
</script>

