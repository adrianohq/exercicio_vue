<script setup>
import { reactive } from 'vue';


const estado = reactive({
  numero1: '',
  numero2: '',
  operacao: 'soma'
});

const calcularResultado = () => {
  switch (estado.operacao) {
    case 'soma':
      return estado.numero1 + estado.numero2;
    case 'subtracao':
      return estado.numero1 - estado.numero2;
    case 'multiplicacao':
      return estado.numero1 * estado.numero2;
    case 'divisao':
      return estado.numero2 !== 0 ? estado.numero1 / estado.numero2 : 'Erro: Divisão por zero';
    default:
      return 'Operação inválida';
  }
};
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-success text-light rounded-3">
      <h1>Calculadora VueJS</h1>
      <p>Para calcular, insira os valores abaixo e selecione a operação desejada</p>
    </header>
    <form class="bg-light pb-4 pt-4">
      <div class="row d-flex justify-content-center align-items-center">
        <div class="col-1">
          <input v-model.number="estado.numero1" type="number" class="form-control">
        </div>
        <div class="col-auto">
          <select v-model="estado.operacao" class="form-select">
            <option value="soma">+</option>
            <option value="subtracao">-</option>
            <option value="multiplicacao">*</option>
            <option value="divisao">/</option>
          </select>
        </div>
        <div class="col-1">
          <input v-model.number="estado.numero2" type="number" class="form-control">
        </div>
        <div class="col-2">
          <div class="form-control col-2" readonly >O resultado é: {{ calcularResultado() }}</div>
        </div>
      </div>
    </form>
  </div>
</template>

<style scoped>

</style>
