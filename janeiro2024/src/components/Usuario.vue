<script setup>
import { ref } from "vue";
const nome = ref("Wellington dos santos silva");
</script>

<template>
  <div>
    <form class="formulario">
      <label for="nome">Nome</label><br />
      <input type="text" id="nome" name="nome" v-model="nome" /><br />
    </form>
  </div>

  <p style="text-align: center;">{{ nome }}</p>
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
