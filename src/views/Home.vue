<template>
  <div class="container">
    <div class="content">
      <div class="header">
        <Header title="Task manager" />
        <AddTask @add-task="addTask" />
      </div>
      <div class="tasks-section">
        <Tasks
          @delete-task="deleteTask"
          @toggle-reminder="toggleReminder"
          :tasks="tasks"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Header from '../components/Header.vue';
import Tasks from '../components/Tasks.vue';
import AddTask from '../components/AddTask.vue';
import { mockTask } from '@/mocks/tasks';

export default {
  name: 'HomePage',
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
    };
  },
  created() {
    this.tasks = mockTask;
  },
  methods: {
    addTask(task) {
      this.tasks.push(task);
    },

    deleteTask(id) {
      if (!confirm('Are you sure?')) return;
      this.tasks = this.tasks.filter((task) => task.id !== id);
      console.log(this.tasks);
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
  },
};
</script>

<style scope>
.container {
  margin-top: 25px;
  width: 90vw;
  border: 1px solid black;
}
.content {
  margin: 15px 25px;
}

.header {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;
  padding: 15px 0;
}

.tasks-section {
  display: flex;
  flex-direction: column;
}
</style>
