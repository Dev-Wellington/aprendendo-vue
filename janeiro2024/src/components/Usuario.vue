<script setup>
import { ref } from "vue";


const nome = ref("Wellington dos santos silva");
const dataNascimento = ref(0);
const idade = ref(19);
const idadeFutura = ref(0);
//para acessar o valor de uma variavel reativa, basta usar o .value
console.log(idade.value);
//para alterar o valor de uma variavel reativa, basta usar o .value

function calcularIdade() {
  idade.value = 2023 - dataNascimento.value;
}

const calcularIdadeFutura = (valor) => {
  idadeFutura.value =  idade.value + valor
};

</script>

<template>
  <div>
    <form class="formulario">
      <label for="nome">Nome</label><br />
      <input type="text" id="nome" name="nome" v-model="nome" /><br />
      <label for="dataNascimento">Nascimento</label><br />
      <input
        type="number"
        id="dataNascimento"
        name="dataNascimento"
        v-model="dataNascimento"
      /><br />
    </form>
  </div>

  <button class="botao" v-on:click="calcularIdade()">Calcular idade</button>
  <button class="botao" v-on:click="calcularIdadeFutura(2)">Calcular idade futura</button>

  <p style="text-align: center">{{ nome }} nasceu em {{ dataNascimento }} tem {{ idade }} anos</p>
  <p>Daqui a dois anos terá {{ idadeFutura }}</p>
</template>

<style scoped>
.formulario {
  margin: 0 auto;
  padding: 5px;
  text-align: center;
  width: 200px;
  background-color: blue;
}
</style>
