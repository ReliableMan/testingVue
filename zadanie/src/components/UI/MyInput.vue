<template>

  <input 
  :value="modelValue" 
  @input="updateInput" 
  class="input">

</template>

<script>
export default {
  name: "my-input",
  props: {
    modelValue: [String, Number]
  },
  methods: {
    updateInput(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>

<style scoped>

.input{
  width: 50%;
  border: 1px solid teal;
  padding: 4px 8px 
}

</style>
