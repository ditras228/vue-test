<template>
  <div>
    <button class="btn">
      <slot/>
    </button>
  </div>
</template>

<script>
export default {
  name: 'button-rounded'
}
</script>

<style scoped>
  .btn{
    height: 36px;
    left: 220px;
    top: 312px;

    background: linear-gradient(255.35deg, #DC3131 0.83%, rgba(255, 79, 79, 0) 108.93%), #FF5E56;
    border-radius: 50px;

    color: #FFFFFF;

    cursor: pointer;
  }
</style>