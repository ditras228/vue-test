<template>
  <button class="btn">
    <slot/>
  </button>
</template>

<script>
export default {

}
</script>

<style scoped>
  .btn{
    width: 198px;
    padding: 16px 32px;
    border: 1px solid #FFFFFF;
    filter: drop-shadow(0px 0px 44px #CFDAE7);
    background-color: unset;
    border-radius: 6px;
    color: #FFFFFF;
    font-size: 16px;
    align-self: center;
    cursor: pointer;

    transition: 0.3s;
  }
  .btn:hover{
    background-color: #FFFFFF;
    color: #000000;
  }
</style>