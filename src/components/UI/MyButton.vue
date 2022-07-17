<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'my-button'
};
</script>

<style scoped>
.btn {
  align-self: flex-end;
  margin-left: 10px;
  padding: 10px 15px;
  background: none;
  color: red;
  border: 2px solid red;
  cursor: pointer;
}
</style>

