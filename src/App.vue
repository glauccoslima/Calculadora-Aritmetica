<script setup>
// Importa as funções reativas do Vue.js
import { reactive, computed } from 'vue';

// Cria um objeto reativo para armazenar e atualizar as variáveis de estado
const estado = reactive({
  numero1: 0,  // Estado inicial para o primeiro número
  numero2: 0,  // Estado inicial para o segundo número
  operacao: '+' // Estado inicial para a operação (soma)
});

// Computa o resultado da operação baseado no estado atual dos números e da operação selecionada
const resultado = computed(() => {
  switch (estado.operacao) {
    case '+':
      return estado.numero1 + estado.numero2;
    case '-':
      return estado.numero1 - estado.numero2;
    case '*':
      return estado.numero1 * estado.numero2;
    case '/':
      // Verifica se o segundo número é zero para evitar uma divisão por zero
      return estado.numero2 !== 0 ? estado.numero1 / estado.numero2 : "Divisão por zero não é permitida";
    default:
      return '';
  }
});
</script>

<template>
<!-- Estrutura HTML para a interface de usuário -->
<div class="container mt-5">
  <!-- Define uma linha centralizada -->
  <div class="row justify-content-center">
    <!-- Define uma coluna que ocupa toda a linha em telas pequenas (sm) e metade da linha em telas médias (md) -->
    <div class="col-sm-12 col-md-6">
      <!-- Grupo de controle para o primeiro número -->
      <div class="form-group">
        <label for="numero1">Número 1:</label>
        <input id="numero1" type="number" v-model.number="estado.numero1" class="form-control">
      </div>

      <!-- Grupo de controle para o segundo número -->
      <div class="form-group">
        <label for="numero2">Número 2:</label>
        <input id="numero2" type="number" v-model.number="estado.numero2" class="form-control">
      </div>

      <!-- Grupo de controle para a seleção da operação -->
      <div class="form-group">
        <label for="operacao">Operação:</label>
        <select id="operacao" v-model="estado.operacao" class="form-control">
          <option value="+">Adição (+)</option>
          <option value="-">Subtração (-)</option>
          <option value="*">Multiplicação (*)</option>
          <option value="/">Divisão (/)</option>
        </select>
      </div>

      <!-- Exibe o resultado da operação -->
      <h2>Resultado: {{ resultado }}</h2>
    </div>
  </div>
</div>
</template>

<style scoped>
/* Estilos específicos para este componente */
</style>
