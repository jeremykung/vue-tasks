<template>
    <div :key="task.id" v-for="task in tasks">
        <Task 
            :task='task' 
            @toggle-reminder="id => $emit('toggle-reminder', id)" 
            @del-task="id => $emit('del-task', id)" 
        />
    </div>
</template>

<script>
import Task from './Task'

export default {
    name: 'Tasks',
    props: {
        tasks: Array
    },
    components: {
        Task
    },
    emits: ['del-task', 'toggle-reminder']
}
</script>