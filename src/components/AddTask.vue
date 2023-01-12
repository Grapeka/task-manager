<template>
  <div class="addtaskContainer">
    <input
      v-model="taskTitle"
      class="input"
      type="text"
      placeholder="Task name..."
    />
    <Button @click="addTask" text="Add task" color="green" />
  </div>
</template>
<script>
import Button from './Button.vue';
export default {
  name: 'AddTaskComponent',
  props: {
    onAdd: Function,
  },
  components: {
    Button,
  },
  data() {
    return {
      taskTitle: '',
    };
  },
  methods: {
    addTask() {
      if (!this.taskTitle) {
        alert('Please add a task');
        return;
      }
      const id = Math.floor(Math.random() * 1000000000000) + 1;
      const date = new Date();
      const newTask = {
        id: id,
        title: this.taskTitle,
        day: date.toLocaleDateString(),
        reminder: false,
      };
      console.log(newTask);
      this.$emit('add-task', newTask);
    },
  },
};
</script>
<style scope>
.addtaskContainer {
  display: flex;
  flex-direction: row;
  gap: 12px;
}

.input {
  height: 30px;
  font-size: 0.9rem;
  border-radius: 5px;
}
.input:focus {
  border: 2px solid green;
}
</style>
