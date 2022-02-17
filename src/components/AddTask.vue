<template>
    <div class="add-task">
        <form @submit="addTask">
            <input 
                type="text" 
                class="reminder-input" 
                placeholder="Write here..."
                v-model="text"
            >
            <Button text="Add" class="add-reminder-btn" />
        </form>
        <div class="error-msg">{{errorMsg}}</div>
    </div>
</template>

<script>
import Button from './Button.vue'

export default {
    name: 'AddTask',
    components: {Button},
    data() {
        return {
            text: '',
            errorMsg: ''
        }
    },
    methods: {
        addTask(e) {
            e.preventDefault()
            if (!this.text) {
                this.errorMsg = 'Reminder cannot be blank'
                return
            }

            const newReminder = {
                id: 0,
                text: this.text,
                reminder: true,
            }

            this.$emit('new-reminder', newReminder)
        }
    }
}
</script>

<style>
    .add-task {
        /* background-color: pink; */
        width: 50%;
        min-width: 400px;
        margin: auto;
        border-left: 6px solid #064a5f;
    }
    .add-task > form {
        display: flex;
        justify-content: space-between;
    }
    .reminder-input {
        font-size: 1.02rem;
        border: none;
        border-radius: 5px;
        padding: 0.5rem 1rem;
        margin: 1rem;
        width: 100%;
    }
    .reminder-input:focus {
        outline: none;
    }
    .add-reminder-btn {
        border-radius: 3px;
    }
</style>