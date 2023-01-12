<template>
  <div
    @click="toggleReminder(task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <h4>
      {{ task.title }}<i @click="onDelete(task.id)" class="fas fa-times"></i>
    </h4>
    <p>{{ task.day }}</p>
  </div>
</template>
<script>
export default {
  name: 'TaskComponent',
  props: {
    task: Object,
  },
  data() {
    return {
      clickCounter: 0,
      clickTimeout: null,
    };
  },
  methods: {
    onDelete(id) {
      this.$emit('delete-task', id);
    },
    toggleReminder(id) {
      this.clickCounter++;
      if (this.clickCounter === 1) {
        this.clickTimeout = setTimeout(() => {
          this.clickCounter = 0;
        }, 300);
      } else if (this.clickCounter === 2) {
        clearTimeout(this.clickTimeout);
        this.clickCounter = 0;

        this.$emit('toggle-reminder', id);
      }
    },
  },
};
</script>

<style scope>
.fas {
  color: red;
}

.task {
  display: flex;
  flex-direction: column;
  gap: 5px;
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task h4 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.task.reminder {
  border-left: 5px solid green;
}

p {
  font-size: 0.8rem;
}
</style>
