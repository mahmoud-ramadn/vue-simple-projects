<script setup>
import { computed, ref } from "vue"



const   showing=ref('0')


const appendToDisplay = (vale) => {

    if (showing.value === "0" && vale !== ".") {
        showing.value=vale
    } else {
        showing.value+=vale
    }

    
}



const calculate = () => {
    try {
        showing.value=eval(showing.value).toString();

    } catch{
        showing.value="0"
    }
}



const displayClass = computed(() => {
    return showing.value.length >12 ? "small-text":""
})




const clearDisplay = () => {
    showing.value ="0"
}




</script>

<template>
<div>
<div class="calculator">
<input v-model="showing" type="text" readonly :class="displayClass" >

<div class="buttons">

    <button @click="appendToDisplay('7')">7</button>
        <button @click="appendToDisplay('8')">8</button>
        <button @click="appendToDisplay('9')">9</button>
        <button @click="appendToDisplay('/')">/</button>

        <button @click="appendToDisplay('4')">4</button>
        <button @click="appendToDisplay('5')">5</button>
        <button @click="appendToDisplay('6')">6</button>
        <button @click="appendToDisplay('*')">*</button>

        <button @click="appendToDisplay('1')">1</button>
        <button @click="appendToDisplay('2')">2</button>
        <button @click="appendToDisplay('3')">3</button>
        <button @click="appendToDisplay('-')">-</button>

        <button @click="appendToDisplay('0')">0</button>
        <button @click="appendToDisplay('.')">.</button>
        <button @click="calculate()">=</button>
        <button @click="appendToDisplay('+')">+</button>

</div>

<button @click="clearDisplay" class="clear-button">C</button>

</div>

</div>
















</template>
<style scoped>
input {
  padding: 10px 20px;
  margin-bottom: 20px;
}

.calculator {
  max-width: 300px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.display {
  width: 100%;
  margin-bottom: 10px;
  padding: 10px;
  font-size: 18px;
  text-align: right;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

button {
  width: 100%;
  padding: 10px;
  font-size: 18px;
}

.clear-button {
  width: 100%;
  margin-top: 10px;
}

.small-text {
  font-size: 14px;
}
</style>