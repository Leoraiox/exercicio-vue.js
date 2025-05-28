<script setup>
import { ref, computed } from "vue";

const num1 = ref(null);
const num2 = ref(null);
const operacao = ref("+");

const resultado = computed(() => {
  if (num1.value === null || num2.value === null) return "Digite os valores";
  switch (operacao.value) {
    case "+": return num1.value + num2.value;
    case "-": return num1.value - num2.value;
    case "*": return num1.value * num2.value;
    case "/": return num2.value !== 0 ? num1.value / num2.value : "Erro (divisão por zero)";
    default: return 0;
  }
});
</script>

<template>
  <div class="container">
    <div class="device">
      <div class="screen">
        <h2>Calculadora Aritmética</h2>
        <input type="number" v-model="num1" placeholder="Número 1" />
        <input type="number" v-model="num2" placeholder="Número 2" />
        <select v-model="operacao">
          <option value="+">+</option>
          <option value="-">-</option>
          <option value="*">×</option>
          <option value="/">÷</option>
        </select>
        <h3>Resultado: {{ resultado }}</h3>
      </div>
    </div>
  </div>
</template>



<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: linear-gradient(135deg, #1d1f21, #36393f);
}
.device {
  width: 400px;
  height: 600px;
  background: #222;
  border-radius: 30px;
  box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.3);
  position: relative;
}
.device::before {
  content: "";
  position: absolute;
  width: 80px;
  height: 8px;
  background: #444;
  border-radius: 8px;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
}
.screen {
  width: 90%;
  height: 80%;
  margin: 20px auto;
  background: #eee;
  border-radius: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
input, select {
  display: block;
  margin: 10px;
  padding: 8px;
  font-size: 18px;
  border: 1px solid #ccc;
  border-radius: 5px;
}
h2, h3 {
  color: #333;
}
</style>