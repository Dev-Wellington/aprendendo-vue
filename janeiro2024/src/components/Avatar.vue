<script setup>
import { ref, reactive, computed ,onMounted } from "vue";

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
const codigoUsuario = ref(0);

onMounted(async () => {
  pessoa.value = await buscarInformacoes(1);
});


const habilitarBotao = computed(()=> codigoUsuario.value > 0)

const nomeCompleto = computed(() => 
  `${pessoa.value.first_name} ${pessoa.value.last_name}`
);

const pesquisarInformacoes = async () => {
  pessoa.value = await buscarInformacoes(codigoUsuario.value);
};

const buscarInformacoes = async (id) => {
  const req = await fetch(`https://reqres.in/api/users/${id}`);
  const json = await req.json();
  return json.data;
};


</script>
<template>
  <form class="formulario" @submit.prevent>
    <label for="codigoUsuario"></label><br />
    <input
      type="text"
      id="codigoUsuario"
      name="codigoUsuario"
      v-model="codigoUsuario"
    /><br />
    <button v-bind:disabled="!habilitarBotao" v-on:click="pesquisarInformacoes" class="botao">Buscar</button>
  </form>
  <div class="perfil">
    <img v-bind:src="pessoa.avatar" alt="perfil"  />
    <strong>{{ nomeCompleto }}</strong>
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
.formulario {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.botao {
  padding: 10px;
  border-radius: 5px;
  border: none;
  background-color: #f5f5f5;
  font-size: 1.5rem;
  font-family: Geneva, Tahoma, sans-serif;
  cursor: pointer;
}
.botao[disabled]{
  background-color: #ccc;
  color: #fff;
  cursor: not-allowed;
}
</style>
