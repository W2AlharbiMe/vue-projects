<template>
  <div @dblclick="handleReminderToggle" :class="[task.reminder && 'reminder', 'task']">
      <h3>{{ task.text }}
          <i @click="handleTaskDelete" class="fas fa-times"></i>
      </h3>
      <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
    name: 'Task',
    emits: ['onTask:delete', 'onTask:toggle'],
    props: {
      task: Object
    },
    methods: {
      handleTaskDelete() {
        this.$emit('onTask:delete', this.task.id);
      },
      handleReminderToggle() {
        this.$emit('onTask:toggle', this.task.id);
      }
    }
}
</script>

<style scoped>
.fas {
  color: red;
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
