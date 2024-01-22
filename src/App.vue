<script setup>
import { reactive } from 'vue';

  const estado = reactive({
    filtro: 1,
    num1: 0,
    num2: 0,
    resultado: 0
  })

  function somar() {
    return estado.resultado = parseInt(estado.num1) + parseInt(estado.num2);
  }

  function subtrair() {
    return estado.resultado = estado.num1 - estado.num2;
  }

  function multiplicar() {
    return estado.resultado = estado.num1 * estado.num2;
  }

  function dividir() {
    return estado.resultado = estado.num1 / estado.num2;
  }

  const getOperacao = () => {
    const { filtro } = estado;

    switch (filtro) {
      case "1":
        return somar();
      case "2":
        return subtrair();
      case "3":
        return multiplicar();
      case "4":
        return dividir();
    }
  }
</script>

<template>
  <div class="container text-center">
    <h1 class="m-5">Calculadora</h1>
    <div class="row">
      <div class="col-md-4">
        <input class="form-control" type="number" placeholder="Digite um número" @keyup="evento => estado.num1 = evento.target.value">
      </div>
      <div class="col-md-2">
        <select class="form-control" @change="evento => estado.filtro = evento.target.value">
          <option class="fs-3" value="1">+</option>
          <option class="fs-3" value="2">-</option>
          <option class="fs-3" value="3">x</option>
          <option class="fs-3" value="4">÷</option>
        </select>
      </div>
      <div class="col-md-4">
        <input class="form-control" type="number" placeholder="Digite um número"  @keyup="evento => estado.num2 = evento.target.value">
      </div>
      <div class="col-md-1">
        <h3>=</h3>
      </div>
      <div class="col-md-1">
        <h3>{{ getOperacao(estado.resultado) }}</h3>
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>