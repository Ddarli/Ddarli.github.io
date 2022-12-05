<template>
  <button  class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "my-button",
};
</script>

<style scoped>
.btn {
  background: none;
  border: none;
  font-size: 15px;
  color: white;
  cursor: pointer;
}
</style>