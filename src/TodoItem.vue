<template>
    <p>
        <span>{{ item.description }}</span>
        <b-button variant="danger" @click="$emit('remove')">remover</b-button>
    </p>
</template>

<script>
export default {
    props: {
        item: Object
    }
}
</script>

