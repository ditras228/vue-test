<template>
    <input :input="modelValue" @input="updateInput" class="input" type="number">
</template>

<script>
export default {
  name: 'my-input',
  props: {
    modelValue: [String, Number]
  },
  methods:{
    updateInput(event){
      this.$emit('update:modelValue',event.target.value)
    }
  }
}
</script>

<style scoped>
  .input{
    border: 1px solid #DFE3E6;
    box-sizing: border-box;
    border-radius: 3px;
    padding: 8px 10px ;
    margin-bottom: 8px;
    height: 40px;
  }
</style>