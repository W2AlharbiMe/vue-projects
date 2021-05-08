<template>
  <form @submit.prevent="handleAddTaskSubmit" class="add-form">
    <div class="form-control">
      <label for="text">Task</label>
      <input type="text" name="text" id="text" placeholder="Add Task" v-model="text" />
    </div>
    <div class="form-control">
      <label for="day">Day & Time</label>
      <input type="text" name="day" id="day" placeholder="Day & Time" v-model="day" />
    </div>
    <div class="form-control-check">
      <label for="reminder">Set Reminder</label>
      <input type="checkbox" name="reminder" id="reminder" v-model="reminder" />
    </div>

    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
    name: 'AddTask',
    emits: ['onTask:add'],
    data: () => ({
      text: '',
      day: '',
      reminder: false,
    }),
    methods: {
      handleAddTaskSubmit(e) {
        const {text, day, reminder} = this;
        this.$emit('onTask:add', { text, day, reminder });

        ['text', 'day', 'reminder'].forEach(k => this[k] = '');
        e.target.reset();
      }
    }
}
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
  margin: 5px;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 5px;
  height: 40px;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  width: 20px;
  height: 20px;
}
</style>
