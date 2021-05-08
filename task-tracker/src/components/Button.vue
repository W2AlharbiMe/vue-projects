<template>
  <button @click="handleToggleForm" :class="className">{{ text }}</button>
</template>

<script>
export default {
    name: 'Button',
    props: ['text', 'className'],
    emits: ['onTask:toggleForm'],
    methods: {
        handleToggleForm() {
            this.$emit('onTask:toggleForm');
        }
    }
}
</script>

<style scoped>

</style>
