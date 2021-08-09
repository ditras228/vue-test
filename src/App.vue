<template>
 <div class="canvas">
   <main-button style="margin: 0 auto" @click="setVisible">Налоговый вычет</main-button>
   <modal v-model:show="dialogVisible"/>
 </div>
</template>

<script>
import Modal from './components/UI/Modal'
import MainButton from "./components/UI/MainButton";
export default {
  components:{
    Modal,
    MainButton,
  },
  data(){
    return {
      dialogVisible: false
    }
  },

  methods:{
    setVisible(){
      this.dialogVisible=true
    }
  },
}
</script>

<style>
*{
  margin: 0;
  box-sizing: border-box;
  font-size:14px
}
button{
  border-color: unset;
  border-style: unset;
}
body{
  background: linear-gradient(255.35deg, #DC3131 0.83%, rgba(255, 79, 79, 0) 108.93%), #FF5E56;
  border-radius: 0;
  font-family: Roboto,sans-serif;
  overflow: hidden;
}
.canvas{
  display: grid;
  height: 100vh;
}
</style>