<template>
  <div class="dialog" v-if="isVisible" @click="hideDialog">
    <div @click.stop class="dialog__content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'my-dialog',
  props: {
    isVisible: {
      type: Boolean,
      default: false
    }
  },

  methods: {
    hideDialog() {
      this.$emit('update:isVisible', false)
    }
  }
}
</script>

<style scoped>
.dialog {
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  display: flex;
}

.dialog__content{
  border: 1px solid black;
  margin: auto;
  background: white;
  border-radius: 12px;
  min-width: 400px;
}
</style>