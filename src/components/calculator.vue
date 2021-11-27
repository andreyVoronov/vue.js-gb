<template>
<div id="app">
 <div class="numbers_container">
   <input type="text" v-model="result" placeholder="0">
   <button @click="input(number)" class="numbers cell" v-for="number in numbers" :key="number">{{number}}</button>
   <button @click="input(operation)" class="operations cell" v-for="operation in operations" :key="operation">{{operation}}</button>
   <button @click="reset()" class="reset cell">R</button>
   <button @click="calculation()" class="operations cell">=</button>
   <button @click="exp()" class="operations cell">exp</button>
 </div>
</div>
</template>

<script>
export default {
  name: 'calculator',
  data: () => (
    {
      result: '',
      numbers : [1,2,3,4,5,6,7,8,9,0],
      operations : ['+','-','*','/','**']
    }
  ),
  methods: {
    input: function(char) {
    this.result+=char;
    },
    reset: function() {
      this.result = ''
    },
    calculation: function() {
     this.result = eval(this.result); 
    },

  }
}
</script>

<style scoped>
#app{
  max-width: 20rem;
}
input[type="text"] {
  width: 20rem;
  height: 2.25rem;
  background-color: rgb(92, 87, 87);
  font-size: 2rem;
  color: #3bbbf9;
}
input::placeholder{
font-size: 2rem;
  color: #3bbbf9;
}
.numbers_container{
  display: flex;                       
  flex-wrap: wrap;  
  justify-content: space-around;
  width: 100%;
}
.cell{ 
  flex: 33%;                       
  height: 8rem;
 font-size: 1rem;
  border: none;
}
.numbers{
  background-color: goldenrod;
}
.numbers:hover{
  background-color: rgb(131, 90, 13);
  transition: 0.5s;
  border: 2px solid rgb(88, 65, 4)
}
.operations{
  background-color: rgb(18, 158, 111);
}
.operations:hover{
   background-color: rgb(6, 75, 52);
  transition: 0.5s;
  border: 2px solid rgb(5, 53, 37);
}
.reset{
  background-color: rgb(107, 7, 7);
}
</style>