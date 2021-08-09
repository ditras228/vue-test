<template>
  <div @click="updateInput">
    <label>
      <input type="checkbox"
             :value="value"
             class="input"
             checked="checked"
      >
      <div class="box">
        <div class="check"/>
      </div>

    </label>
  </div>
</template>

<script>
export default {
  name: 'my-checkbox',
  props: {
    value: {type: String, default: null},
    modelValue: {type: Array, default: () => [],}
  },
  methods: {
    onChange(value) {
      if (this.modelValue.includes(this.value)) {
        this.$emit('update:modelValue', this.modelValue.filter(cv => cv !== value))
      } else {
        this.$emit('update:modelValue', this.modelValue.concat(value))
      }
    }
  }
}
</script>

<style scoped>
.input:hover + .box {
  background-image: url("../img/checkbox_hover.png");
}

.input:disabled + .box {
  background-image: url("../img/checkbox_disabled.png");
}

.check {
  width: 20px;
  height: 20px;
  margin: 0 auto;
  align-self: center;
  background-image: url("../img/check.png");
  background-repeat: no-repeat;
  background-position: center;
}

.input {
  position: absolute;
  display: none;
}

.input:checked + .check {
  width: 20px;
  height: 20px;
  background-image: url("../img/check.png");
  background-repeat: no-repeat;
  background-position: center;

}
.box{
  width: 20px;
  height: 20px;
  background-image: url("../img/checkbox_normal.png");

}
.input:checked + .box {
  background-image: url("../img/checkbox_true.png");
  border-radius: 6px;
  display: grid;
}
</style>