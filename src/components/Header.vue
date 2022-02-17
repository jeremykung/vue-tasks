<template>
    <header>
        <h1>{{ title }}</h1>
    </header>
</template>

<script>
export default {
    name: 'Header',
    props: {
        title: {
            type: String,
            default: 'Title'
        }
    }
}
</script>

<style>
    header {
        padding: 1rem;
    }
</style>