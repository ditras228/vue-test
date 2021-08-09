<template>
  <div @click="updateInput"  class="box">
    <label>
      <input type="checkbox"
             :value="value"
             class="input"

      >
      <div class="check"/>
    </label>

  </div>
</template>

<script>
export default {
  name: 'my-checkbox',
  props:{
    value:{type: String, default: null},
    modelValue:{type: Array,default: ()=>[],}
  },
  methods:{
    onChange(value){
      if(this.modelValue.includes(this.value)){
        this.$emit('update:modelValue',this.modelValue.filter(cv=>cv!==value))
      }else{
        this.$emit('update:modelValue',this.modelValue.concat(value))
      }
    }
  }
}
</script>

<style scoped>
.box{
  width: 20px;
  height: 20px;
  background: linear-gradient(255.35deg, #DC3131 0.83%, rgba(255, 79, 79, 0) 108.93%), #FF5E56;
  border-radius: 6px;
  display: grid;
}
.check{
  margin: 0 auto;
  align-self: center;
}
.input{
  display: none;
  position: absolute;
}
.input:checked + .check{
  width: 20px;
  height: 20px;
  background-image: url("../img/check.png");
  background-repeat: no-repeat;
  background-position: center;
}
</style>