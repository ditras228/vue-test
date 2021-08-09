<template>
  <div class="line">
    <my-checkbox :value="value"/>
    <div><span class="mark">{{item.value}} рублей</span> в {{ item.id+1 }} год</div>
  </div>
</template>

<script>

export default {
  name: 'my-line',
  props:{
    item:{
      value:true,
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
  .line{
    display: grid;
    grid-template-columns: auto 1fr;
    grid-gap: 10px;

    margin-top: 16px;
    padding-bottom: 20px;
    border-bottom: 1px solid gray;
  }
  .mark{
    font-weight: 700;
  }
</style>