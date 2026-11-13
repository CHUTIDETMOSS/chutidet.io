<script setup lang="ts">
import { ref } from 'vue'
const d = ref('0')
const add = v => d.value = d.value === '0' ? v : d.value + v
const calc = () => {
  try { d.value = String(eval(d.value)) }
  catch { d.value = 'Error' }
}
const clear = () => d.value = '0'
</script>

<template>
  <div>
    <p>{{ d }}</p>
    <button @click="add('1')">1</button>
    <button @click="add('2')">2</button>
    <button @click="add('3')">3</button>
    <button @click="add('4')">4</button>
    <button @click="add('5')">5</button>
    <button @click="add('6')">6</button>
    <button @click="add('7')">7</button>
    <button @click="add('8')">8</button>
    <button @click="add('9')">9</button>
    <button @click="add('/')">/</button>
    <button @click="add('0')">0</button>
    <button @click="add('.')">.</button>
    <button @click="calc()">=</button>
    <button @click="add('*')">*</button>
    <button @click="add('-')">-</button>
    <button @click="add('+')">+</button>
    <button @click="clear()">C</button>
  </div>
</template>
