<template>
  <div>
    <div>
      <input type="number" v-model.number="op1">
      <input type="number" v-model.number="op2">
      = {{ result }}
    </div>
    <div>
      <button @click="result = op1 + op2">+</button>
      <button @click="sub">-</button>
      <button @click="div">/</button>
      <button @click="mult">*</button>
      <button @click="exp">exp</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Calc',
  data: () => ({
    op1: 0,
    op2: 0,
    result: 0,
  }),
  methods: {
    sub() {
      this.result = this.op1 - this.op2;
    },
    div() {
      if(this.op2 === 0){
          this.result = 'вы ввели недопустимое значение'
      }
      else{
          this.result = this.op1 / this.op2;
      }
    },
    mult() {
      this.result = this.op1 * this.op2;
    },
    exp() {
        this.result = this.op1 ** this.op2;
    }
  },
};
</script>