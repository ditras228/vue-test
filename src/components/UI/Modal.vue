<template>
  <div class="dark"  v-if="show">
  <div class="modal">
    <img src="../img/close.png" class="close" @click="hideDialog"/>
    <div class="tittle_modal">Налоговый вычет</div>
    <div class="desc">Используйте налоговый вычет чтобы погасить ипотеку досрочно. Размер налогового вычета составляет
      не более 13% от своего официального годового дохода.
    </div>
    <div>
      <div class="title">Ваша зарплата в месяц</div>
      <my-input placeholder="Введите данные" v-model="salary" class="input"/>
      <div @click="calc" class="tittle_red">Рассчитать</div>
    </div>
    <div>
      <div class="total">
        <my-line v-for="item in items"
                 :item="item"
                 :key="item.id"/>
      </div>

      <div class="settings">
        <div>Что уменьшаем?</div>
        <div class="settings_btns">
          <button-rounded>Платеж</button-rounded>
          <button-rounded-white class="btn_rounded">Срок</button-rounded-white>
        </div>

      </div>
    </div>
    <my-button class="btn">Добавить</my-button>

  </div>
  </div>
</template>
<script>
export default {
  name: 'modal',
  props: {
    show: {
      type: Boolean,
      default: true
    }
  },
  data() {
    return {
      salary: 0,
      deduction: 0,
      price: 2000000,
      items: []
    }
  },
  methods: {
    calc() {
      const newCalc = []
      let years
      let remainder
      this.deduction = (this.salary * 12) * 0.13
      years = this.price * 0.13 / this.deduction
      remainder = this.price * 0.13 % this.deduction
      if (this.price >= 2000000) {
        if (this.deduction > 260000) {
          years = 260000 / this.deduction
          remainder = 260000 % this.deduction

        }
      }


      let i = 0
      for (i; i < Math.ceil(years) - 1; i++) {
        newCalc.push({id: i, value: this.deduction})
      }
      if (remainder) {
        newCalc.push({id: i, value: Math.floor(remainder)})
      } else {
        newCalc.push({id: i, value: this.deduction})
      }
      this.items = newCalc
    },
    hideDialog() {
      this.$emit('update:show', false)
    }
  }
}
</script>

<style>
.modal {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  width: 552px;
  min-height: 476px;

  background: #FFFFFF;
  border-radius: 30px;

  display: grid;

  padding: 32px;
}

.tittle_modal {
  width: 235px;
  height: 40px;

  font-size: 28px;
  line-height: 40px;
}

.desc {
  width: 369px;
  height: 72px;
  left: 32px;
  top: calc(50% - 72px / 2 - 114px);
  line-height: 24px;
  color: #808080;

  margin-bottom: 24px;
}

.close {
  position: absolute;
  right: 27px;
  top: 27px;
}

.title {
  font-weight: 500;
  margin-bottom: 8px;
}

.btn {
  width: 100%;
}

.tittle_red {
  color: #EA0029;
}

.tittle_red {
  cursor: pointer;
}

.input {
  width: 100%;
}

.total {
  margin-bottom: 20px;
}

.settings {
  display: grid;
  grid-template-columns: 112px 1fr;
  grid-column-gap: 10px;

  width: 242px;
  margin-bottom: 48px;
  align-items: center;

}
.settings_btns{
  display: grid;
  grid-template-columns: 73px 57px;
  grid-gap: 16px;
}
.dark{
  width:100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.3);
  position: absolute;

}
@media screen and (min-width: 768px){
    .modal{
      width: 453px;
    }
}
@media screen and (max-width: 320px){
  .modal{
    position: relative;
    left: 0;
    right: 0;
    top: 0;
    transform: translate(0, 0);
    width: 100%;
    height: 100vh;
    border-radius: 0;
    padding: 16px;
    grid-gap: 20px;
    grid-template-rows: 44px 90px auto 1fr;
  }
  .desc{
    width: 288px;
    font-size: 12px;
  }
  .settings{
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 1fr ;
  }
  .settings_btns{
    grid-template-columns: 73px 57px;
    grid-gap: 8px;
  }
}
</style>