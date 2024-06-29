<template>
  <button @click="incrementCounter">Adicione 1</button>
  <button @click="decrementCounter">Remova 1</button>
  <p v-show="message">{{ message }}</p>
</template>

<script setup>
import { ref, watch } from "vue";

const counter = ref(0);
const message = ref("");

function incrementCounter() {
  if (counter.value === 20) alert("O contador só pode ir até 20");
  if (counter.value < 20) counter.value++;
}

function decrementCounter() {
  if (counter.value === 0) alert("O contador só pode ir até zero");
  if (counter.value > 0) counter.value--;
}

watch(counter, (newValue, oldValue) => {
  if (newValue === 0) {
    message.value = "";
  } else if (newValue === 1) {
    message.value = `O botão foi clicado: ${newValue} vez.`;
  } else {
    message.value = `O botão foi clicado: ${newValue} vezes.`;
  }
});
</script>
