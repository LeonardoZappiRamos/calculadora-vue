<script setup>
import { reactive } from 'vue';

const estado = reactive({
  valorUm: 0,
  valorDois: 0,
  operacao: '+'
})

const aritimetica = () => {
  switch(estado.operacao) {
    case '+':
      return parseInt(estado.valorUm) + parseInt(estado.valorDois);
    case '-':
      return parseInt(estado.valorUm) - parseInt(estado.valorDois);
    case '*':
      return Math.round(parseInt(estado.valorUm) * parseInt(estado.valorDois));
    case '/':
      return Math.round(parseInt(estado.valorUm) / parseInt(estado.valorDois));
    default:
      return "0";
  }
}

const entenda = () => {
  switch(estado.operacao) {
    case '+':
      return "A adição é uma operação matemática considerada básica, consiste em acrescentar uma certa quantia a outra já existente.";
    case '-':
      return "Subtração é uma operação matemática que indica quanto é um valor numérico se dele for removido outro valor numérico.";
    case '*':
      return "Na matemática, a multiplicação é uma forma simples de se adicionar uma quantidade finita de números iguais.";
    case '/':
      return "Divisão é a operação matemática inversa da multiplicação.";
    default:
      return "As operações matemáticas básicas são adição, subtração, multiplicação e divisão";
  }
}
</script>

<template>
  <main class="container">
    <div class="bg">
      <h1>Calculadora Aritmética</h1>
      <form class="form form-inline">
        <div  class="form-group mb-2" >
          <input @keyup="evento => estado.valorUm = evento.target.value" type="number" class="form-control text-center" placeholder="Primeiro Valor"/>
        </div>
        <div class="form-group mb-2">
          <select @change="evento => estado.operacao = evento.target.value" class="form-control text-center" id="operacao">
            <option disabled>Please select one</option>
            <option>+</option>
            <option>-</option>
            <option>*</option>
            <option>/</option>
          </select>
        </div>
        <div class="form-group mb-2" >
          <input @change="evento => estado.valorDois = evento.target.value" type="number" class="form-control text-center" placeholder="Segundo Valor"/>
        </div>
      </form>
      <div class="content">
        <p>Resultado: {{ aritimetica() }}</p>
        <p>Entenda: {{ entenda() }}</p>
      </div>
    </div>
  </main>
</template>

<style scoped>
  main {
    background-color: #e7eed0;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .bg {
    background-color: #cad1c3;
    border: 5px solid #2e1437;
    border-radius: 20px;
    max-width: 640px;
    max-height: 640px;
    padding: 1em;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .content{
    margin-top: 0.5em;
    text-align: center;
  }

  .content p:last-child {
    text-align: justify;
  }
</style>
