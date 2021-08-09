<template>
  <div>
    <button class="btn">
      <slot/>
    </button>
  </div>
</template>

<script>
export default {
  name: 'my-button'
}
</script>

<style scoped>
.btn{
  height: 56px;

  background: linear-gradient(255.35deg, #DC3131 0.83%, rgba(255, 79, 79, 0) 108.93%), #FF5E56;
  box-shadow: 0 0 24px rgba(234, 0, 41, 0.33);
  border-radius: 6px;

  font-size: 16px;
  color: #FFFFFF;

  cursor: pointer;
}
</style>