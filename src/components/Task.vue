<template>
    <div 
        @dblclick="toggleReminder(task.id)" 
        :class="['single-task', task.reminder ? 'reminder' : '']"
    >
        <h2>{{task.id}}</h2>
        <h3>{{task.text}}</h3>
        <h4 @click='onDelete(task.id)' class="del-btn">x</h4>
    </div>
</template>

<script>
export default {
    name: 'Task',
    props: {
        task: Object
    },
    methods: {
        onDelete(id) {
            this.$emit('del-task', id)
        },
        toggleReminder(id) {
            this.$emit('toggle-reminder', id)
        }
    }
}
</script>

<style>
    .single-task {
        display: flex;
        align-items: center;
        background-color: lightgrey;
        width: 50%;
        min-width: 400px;
        margin: 1rem auto;
        border-left: 6px solid lightgrey;
    }
    .single-task > h2 {
        padding: 0.5rem 1rem;
    }
    .single-task > h4 {
        margin-left: auto;
        padding: 0.5rem 1rem;
        cursor: pointer;
    }
    .reminder {
        border-left: 6px solid black;
    }
</style>