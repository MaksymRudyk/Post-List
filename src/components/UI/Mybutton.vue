<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'my-button'
}
</script>

<style>
  .btn {
    border: 1px solid teal;
    color: teal;
    width: 100px;
    height: 30px;
    border-radius: 10px;
    background: none;
  }
</style>