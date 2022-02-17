<template>
    <button :style="{background: color}">
        {{text}}
    </button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        text: {
            type: String,
            default: 'Click'
        },
        color: {
            type: String,
            default: '#000'
        },
    },
}
</script>

<style>
    button {
        color: white;
        padding: 0.5rem 1rem;
        border-radius: 5px;
        border: none;
    }
</style>