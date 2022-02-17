<template>
  <div class="container">
    <nav>
      <Header title="Reminders" />
      <Button 
        @click="showAddForm = !showAddForm" 
        :text="showAddForm ? 'Close Form' : 'Add New'" 
      />
    </nav>
    <AddTask 
      v-show="showAddForm" 
      @new-reminder="newReminder => addTask(newReminder)" 
    />
    <Tasks 
      :tasks="tasks"
      @del-task="id => delTask(id)"
      @toggle-reminder="id => toggleReminder(id)"
    />
  </div>
</template>

<script>
import Header from '@/components/Header'
import Button from '@/components/Button'
import Tasks from '@/components/Tasks'
import AddTask from '@/components/AddTask'

export default {
  name: 'App',
  components: { Header, Button, Tasks, AddTask },
  data() {
    return {
      tasks: [],
      showAddForm: false
    }
  },
  methods: {
    delTask(id) {
      this.tasks = this.tasks.filter(task => task.id !== id)
    },
    toggleReminder(id) {
      console.log('toggle', id)
      this.tasks = this.tasks.map(task => task.id === id ? {...task, reminder: !task.reminder} : task)
    },
    addTask(newReminder) {
      this.tasks = [...this.tasks, newReminder]
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Review vue',
        reminder: true
      },
      {
        id: 2,
        text: 'Finish tut',
        reminder: false
      },
      {
        id: 3,
        text: 'Create recipes',
        reminder: true
      }
    ]
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+Display:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

* {
  margin: 0;
  padding: 0;
  font-family: 'Noto Sans Display', sans-serif;
}

nav {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0.5rem;
}
</style>
