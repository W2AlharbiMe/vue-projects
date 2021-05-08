<template>
  <header>
      <h1>{{ title }}</h1>
      <Button @onTask:toggleForm="handleToggleForm" :text="showAddTaskForm ? 'Close' : 'Add Task'" className="btn" />
  </header>
</template>

<script>
import Button from './Button'

export default {
    name: 'Header',
    props: ['title', 'showAddTaskForm'],
    components: { Button },
    methods: {
        handleToggleForm() {
            this.$emit('onTask:toggleForm');
        }
    }
}
</script>

<style scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>
