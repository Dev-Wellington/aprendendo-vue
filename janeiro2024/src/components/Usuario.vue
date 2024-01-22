<script setup>
import { reactive } from "vue";


/*
const nome = ref("Wellington dos santos silva");
const nascimento = ref(0);
const idade = ref(19);
//para acessar o valor de uma variavel reativa, basta usar o .value
console.log(idade.value);
//para alterar o valor de uma variavel reativa, basta usar o .value
*/

//usando objeto reativo
const pessoa = reactive({
  nome: "",
  dataNascimento: 0,
  idade: 0
  
});
//para alterar basta apenas usar pessoa.nome, ou pessoa.dataNascimento

</script>

<template>
  <div>
    <form class="formulario">
      <label for="nome">Nome</label><br />
      <input type="text" id="nome" name="nome" v-model="pessoa.nome" /><br />
      <label for="dataNascimento">Nascimento</label><br />
      <input
        type="number"
        id="dataNascimento"
        name="dataNascimento"
        v-model="pessoa.dataNascimento"
      /><br />
    </form>
  </div>

  <p style="text-align: center">{{ pessoa.nome }} nasceu em {{ pessoa.dataNascimento }}</p>
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
