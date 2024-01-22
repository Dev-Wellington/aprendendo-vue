<template>
  <div>
    <button id="incremento">+1</button>
    <button id="decremento">-1</button>
    <p>{{ contador }}</p>
  </div>
</template>
    <script>
    import { ref } from "vue";
    const contador = ref(0);
    const incremento = document.getElementById("incremento");
    const decremento = document.getElementById("decremento");
    incremento.addEventListener("click", () => {
      contador += 1;
    });
    decremento.addEventListener("click", () => {
      contador -= 1;
    });
    </script>

<style  scoped>
button{
    background-color: red;
}
</style>
