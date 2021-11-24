<template>
  <div class="hello">
    <h1> Calculator </h1>
    <input type="number" v-model.number="num1"/>&nbsp;
    <input type="number" v-model.number="num2"/>
    = {{ result }}
    <div class="error" v-if="error">
        {{ error }}
    </div>
    <div class="operations">
      <div>
        <button v-for="action in operations" :key="action.operation" @click="calculate(action.operation)"> {{ action.sign }} </button>
      </div>
    </div>
    <div class="keyboard">
      <label>
        <input type="checkbox" id="showKeyboard" v-model="showKeyboard">
        Show Keyboard
      </label>
      <div class="buttons" v-if="showKeyboard">
        <button v-for="(button,btn) in buttons" :key="btn" @click="buttonClickHandler(+button)" :data-num="+button"> {{ button }} </button>

        <button @click="eraseDigitClickHandler">&lt;--</button>
      </div>
    </div>
    <div class="operands">
      <label>
        <input type="radio" id="one" :value='+1' v-model="operandChosend">
        Operand 1
      </label>
      <label>
        <input type="radio" id="two" :value='+2' v-model="operandChosend">
        Operand 2
      </label>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
export default {
  name: 'Calculator',
  props: {
    msg: String
  },
  data: () => ({
    num1: '',
    num2: '',
    result: 0,
    showKeyboard: true,
    buttons: ['0','1','2','3','4','5','6','7','8','9'],
    operations: [{ operation: 'add', sign: '+' }, { operation: 'subtract', sign: '-' }, { operation: 'multiply', sign: '*' }, { operation: 'devide', sign: '/' }, { operation: 'modulus', sign: '%' }, { operation: 'power', sign: 'x^y' }],
    operandChosend: 1,
    error: '',
    log: null,
    logs: {}
  }),
  methods: {
    eraseDigitClickHandler () {
    if (this.operandChosend === 1) {
       this.num1 = this.num1.slice(0, this.num1.length - 1)
     } else {
       this.num2 = this.num2.slice(0, this.num2.length - 1)
     }
    },
    buttonClickHandler (num) {
      if (this.operandChosend === 1) {
        this.num1 += num
      } else {
        this.num2 += num
      }
    },
    calculate (op) {
      const { num1, num2 } = this
      this.error = ''
      const operationsMapping = {
        add: () => +num1 + +num2,
        subtract: () => num1 - num2,
        multiply: () => num1 * num2,
        devide: () => {
          if (num2 === 0) {
            this.error = 'Вы ввели недопустимое значение'
          }
          return num1 / num2
        },
        modulus: () => num1 % num2,
        power: () => Math.pow(num1, num2)
      }
      this.result = operationsMapping[op]()
      // this.logs[Date.now()] = `${num1} ${op} ${num2} = ${this.result}`
      Vue.set(this.logs, Date.now(), `${num1} ${op} ${num2} = ${this.result}`)
    }
  }
}
</script>
<style>

</style>