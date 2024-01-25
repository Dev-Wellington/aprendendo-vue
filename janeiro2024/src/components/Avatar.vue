<script setup>
import { ref, reactive, onMounted } from "vue";

//usando reactive
/*
const pessoaReactive = reactive({
  first_name: "",
  last_name: "",
  email: "",
  avatar: "",
});

onMounted(() => {
  pessoaReactive.first_name = "Janeiro";
  pessoaReactive.last_name = "Silva";
  pessoaReactive.email = "teste@teste.email.com";
  pessoaReactive.avatar =
    "https://cdn.pixabay.com/photo/2016/08/08/09/17/avatar-1577909_960_720.png";
});
*/
//usando ref
//pessoa recebe um objeto vazio
const pessoa = ref({});

onMounted(async () => {
  pessoa.value = await buscarInformacoes();
});

const buscarInformacoes = async () => {
  const req = await fetch("https://reqres.in/api/users/2");
  const json = await req.json();
  return json.data;
};

</script>
<template>
  <div class="perfil">
    <img
      v-bind:src="pessoa.avatar"
      alt="perfil"
      height="250px"
      width="250px"
    />
    <strong>{{ pessoa.first_name + pessoa.last_name }}</strong>
    <span>{{ pessoa.email }}</span>
  </div>
</template>

<style scoped>
.perfil {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin: 20px;
}
span {
  font-size: 1.5rem;
  font-family: Geneva, Tahoma, sans-serif;
}
</style>
