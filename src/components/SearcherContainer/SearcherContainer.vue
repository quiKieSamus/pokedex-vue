<script setup>
import { ref } from 'vue';
const pokeNameModel = defineModel();
const pokeData = ref("Pikachu");
async function searchPokemon() {
  const res = await fetch(`https://pokeapi.co/api/v2/pokemon/${pokeNameModel.value ?? "pikachu"}`);
  if (!res.ok) return pokeData.value = false;
  pokeData.value = await res.json();
}

searchPokemon();
</script>

<template>
  <h1> {{ pokeNameModel }} </h1>
  <input type="text" v-on:blur="searchPokemon()" v-model="pokeNameModel" autofocus="true">
</template>
