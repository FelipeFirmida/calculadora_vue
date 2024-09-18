<script>
import { reactive, computed } from 'vue';

export default {
  setup() {
    const state = reactive({
      num1: null,
      num2: null,
      operator: '+',
    });

    const result = computed(() => {
      const a = parseFloat(state.num1);
      const b = parseFloat(state.num2);

      if (isNaN(a) || isNaN(b)) {
        return 'Insira números válidos.';
      }

      switch (state.operator) {
        case'+':
          return a + b;
          break;
        
        case'-':
          return a - b;
          break;

        case'*':
          return a * b;
          break;

        case'/':
          return b !==0 ? a / b: 'Divisão por zero não aceita.';
          break;
      }  
    });

    return {
      state,
      result,
    };
  },
};
</script>

<template>
  <div class="container">
    <h1>Calculadora</h1>
    <form>
      <input class="inputs" v-model="state.num1" id="first-number" type="number" step="any" placeholder="Primeiro Número">

      <select class="inputs inputs--modifier" v-model="state.operator" id="operator">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>

      <input class="inputs" v-model="state.num2" id="first-number" type="number" step="any" placeholder="Segundo Número">
    </form>
    <h2>O resultado é:</h2>
    <p class="resultado"><b>{{ result }}</b></p>
  </div>
</template>

<style scoped>
  .container {
    display: block;
    margin: 0 auto;
    margin-top: 48px;
    max-width: 960px;
  }

  .btn {
    margin-left: 16px;
    background-color: rgb(22, 105, 29);
    padding: 8px 8px;
    border-radius: 8px;
    border: none;
    color: #fff;
    font-weight: bold;
  }

  .btn:hover {
    background-color: rgb(7, 168, 21);
  }

  .inputs {
    padding: 8px;
    font-size: 16px;
  }

  .inputs--modifier {
        font-weight: bolder;
        font-size: 16px;
      }

  .resultado {
    font-size: 32px;
  }
</style>
