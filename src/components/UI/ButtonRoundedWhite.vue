<template>
  <div>
    <button class="btn">
      <div class="text">
        <slot/>
      </div>
    </button>
  </div>
</template>

<script>
export default {
  name: 'button-rounded-white'
}
</script>

<style scoped>
  .btn{
    height: 36px;
    left: 220px;
    top: 312px;

    background: #EEF0F2;
    border-radius: 50px;

    color: #FFFFFF;

    cursor: pointer;
  }
  .text{
    color:#000000;
  }
</style>