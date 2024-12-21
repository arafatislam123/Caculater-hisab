<script setup>
import { ref } from 'vue'

let currentInput = ref('')
let result = ref('')

const append = (char) => {
  currentInput.value += char
}

const clear = () => {
  currentInput.value = ''
  result.value = ''
}

const calculate = () => {
  try {
    result.value = eval(currentInput.value)
  } catch (e) {
    result.value = 'Error'
  }
}
</script>

<template>
  <div class="calculator">
    <div class="display">
      <div class="input">{{ currentInput }}</div>
      <div class="result">{{ result }}</div>
    </div>
    <div class="buttons">
      <button @click="append('1')">1</button>
      <button @click="append('2')">2</button>
      <button @click="append('3')">3</button>
      <button @click="append('+')">+</button>
      <button @click="append('4')">4</button>
      <button @click="append('5')">5</button>
      <button @click="append('6')">6</button>
      <button @click="append('-')">-</button>
      <button @click="append('7')">7</button>
      <button @click="append('8')">8</button>
      <button @click="append('9')">9</button>
      <button @click="append('*')">*</button>
      <button @click="append('0')">0</button>
      <button @click="append('.')">.</button>
      <button @click="clear">C</button>
      <button @click="append('/')">/</button>
      <button @click="calculate">=</button>
    </div>
  </div>
</template>

<style scoped>
.calculator {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.display {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  margin-bottom: 20px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f9f9f9;
}

.input, .result {
  font-size: 2em;
  margin: 5px 0;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

button {
  padding: 20px;
  font-size: 1.5em;
  border: none;
  border-radius: 5px;
  background-color: #4CAF50;
  color: white;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #45a049;
}
</style>