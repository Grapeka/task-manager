<template>
  <div class="container">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'PageLayout',
  props: {},
};
</script>
<style scope>
.container {
  margin-top: 25px;
  width: 90vw;
  border: 1px solid black;
}
</style>
