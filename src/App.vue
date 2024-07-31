<script setup>
import { ref, computed } from 'vue'

const num1 = ref('')
const num2 = ref('')
const operation = ref('addition')

const result = computed(() => {
  const a = parseFloat(num1.value)
  const b = parseFloat(num2.value)
  
  switch (operation.value) {
    case 'addition':
      return a + b
    case 'subtraction':
      return a - b
    case 'multiplication':
      return a * b
    case 'division':
      return b !== 0 ? a / b : 'Erro - Divisão por zero'
    default:
      return ' '
  }
})
</script>

<template>
  <div class="container">
    <div class="calculator">
      <div class="display">
        <h1>Resultado: {{ result }}</h1>
      </div>
  
      <div class="input-group">
        <input type="number" v-model.number="num1" placeholder="Valor A" />
        <input type="number" v-model.number="num2" placeholder="Valor B" />
      </div>
  
      <div class="operation-group">
        <select v-model="operation">
          <option value="addition">Adição</option>
          <option value="subtraction">Subtração</option>
          <option value="multiplication">Multiplicação</option>
          <option value="division">Divisão</option>
        </select>
      </div>
    </div>
  </div>
</template>

<style scoped>

.container{
  display: flex;
  width: 100%;
  justify-content: center;
}

.calculator {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-top: 50px;
  padding: 20px;
  width: 300px;
  background-color: #f7f7f7;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  font-family: Arial, sans-serif;
}

.display {
  background-color: #222;
  color: #fff;
  border-radius: 10px;
  padding: 20px;
  width: 100%;
  text-align: center;
  margin-bottom: 20px;
  box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.2);
}

.input-group {
  display: flex;
  justify-content: space-between;
  width: 100%;
  margin-bottom: 20px;
}

input {
  padding: 10px;
  margin: 5px;
  border: 1px solid #ccc;
  border-radius: 5px;
  width: 48%;
  font-size: 16px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.operation-group {
  width: 100%;
}

select {
  padding: 10px;
  margin: 5px;
  border: 1px solid #ccc;
  border-radius: 5px;
  width: 100%;
  font-size: 16px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

h1 {
  font-size: 24px;
  margin: 0;
}
</style>
