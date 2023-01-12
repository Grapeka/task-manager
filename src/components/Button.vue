<template>
  <button @click="onClick()" :style="{ background: color }" class="btn">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: 'ButtonComponent',
  props: {
    text: String,
    color: String,
  },
  methods: {
    onClick() {
      console.log('Button clicked!');
    },
  },
};
</script>

<style>
.btn {
  padding: 0.7rem;
  border: none;
  border-radius: 5px;
  color: white;
  font-size: 1rem;
  cursor: pointer;
}

.btn:hover {
  transition: 0.1s;
  opacity: 0.9;
}
</style>
