<template>
  <div class="calculadora">
    <h1>Calculadora Aritmética</h1>
    <div class="inputs-container">
      <div class="numeros">
        <input type="number" v-model="numero1" placeholder="Número 1" />
        <input type="number" v-model="numero2" placeholder="Número 2" />
      </div>
      <div class="operacao">
        <select v-model="operacao">
          <option value="+">+</option>
          <option value="-">-</option>
          <option value="*">*</option>
          <option value="/">/</option>
        </select>
      </div>
    </div>
    <div class="resultado">
      <h2>Resultado: {{ resultado }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numero1: 0,
      numero2: 0,
      operacao: '+',
    };
  },
  computed: {
    resultado() {
      const num1 = parseFloat(this.numero1);
      const num2 = parseFloat(this.numero2);

      switch (this.operacao) {
        case '+':
          return num1 + num2;
        case '-':
          return num1 - num2;
        case '*':
          return num1 * num2;
        case '/':
          return num2 !== 0 ? num1 / num2 : 'Erro: Divisão por zero';
        default:
          return 0;
      }
    },
  },
};
</script>

<style scoped>
.calculadora {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  text-align: center;
  border: 1px solid #ccc;
  border-radius: 10px;
  background-color: #f9f9f9;
}

.inputs-container {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px; /* Espaço entre os números e a operação */
}

.numeros {
  display: flex;
  flex-direction: column;
  gap: 10px; /* Espaço entre os campos de número */
}

input, select {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 16px;
  width: 100%; /* Faz os inputs e o select ocuparem a largura total */
}

.operacao {
  display: flex;
  align-items: center; /* Centraliza verticalmente o select */
}

.resultado {
  margin-top: 20px;
  font-size: 20px;
  color: #333;
}
</style>