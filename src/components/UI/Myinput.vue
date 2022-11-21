<template>
  <input :value="value" @input="updateValue" class="input" type="text"/>
</template>

<script>
export default {
  name: 'my-input',
  props: {
    value: [String, Number]
  },

  methods: {
    updateValue(event) {
      this.$emit('update:value', event.target.value)
    }
  }
}
</script>

<style scoped>
  .input {
    width: 90%;
    border: 2px solid teal;
    margin: 5px 5px;
    padding: 5px;
  }
</style>