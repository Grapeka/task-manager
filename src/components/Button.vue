<template>
  <button :style="{ background: color }" class="btn">
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
};
</script>

<style>
.btn {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 35px;
  padding: 0.7rem;
  border: none;
  border-radius: 5px;
  color: white;
  font-size: 0.9rem;
  cursor: pointer;
}

.btn:hover {
  transition: 0.1s;
  opacity: 0.9;
}
</style>
