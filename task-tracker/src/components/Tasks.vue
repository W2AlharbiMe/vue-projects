<template>
    <Task @onTask:delete="handleTaskDelete" @onTask:toggle="handleReminderToggle" v-for="task in tasks" :key="task.id" :task="task" />
</template>

<script>
import Task from './Task'

export default {
    name: 'Tasks',
    props: ['tasks'],
    emits: ['onTask:delete', 'onTask:toggle'],
    components: {
        Task
    },
    methods: {
        handleTaskDelete(id) {
            this.$emit('onTask:delete', id);
        },
        handleReminderToggle(id) {
            this.$emit('onTask:toggle', id);
        }
    }
}
</script>

<style scoped>

</style>
