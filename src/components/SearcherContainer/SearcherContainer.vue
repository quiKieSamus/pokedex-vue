<script setup>
import { ref } from 'vue';
import PokemonDataContainer from '../PokemonDataContainer/PokemonDataContainer.vue';

const pokeNameModel = defineModel();
const pokeData = ref('pikachu');

async function searchPokemon() {
  const res = await fetch(`https://pokeapi.co/api/v2/pokemon/${pokeNameModel?.value?.toLowerCase() ?? "pikachu"}`);
  if (!res.ok) return pokeData.value = false;
  pokeData.value = await res.json();
}

searchPokemon();
</script>

<template class="searcher-container">
  <form>
    <h1> Busco a {{ pokeNameModel || "Pikachu" }} </h1>
    <input type="text" v-model="pokeNameModel" autofocus="true">
    <button v-on:click="(
      (e) => {
        console.log(pokeNameModel);
        e.preventDefault();
        searchPokemon();
      })
      ">Buscar</button>
  </form>
  <PokemonDataContainer :data="pokeData"/>
</template>

<style>
  .searcher-container {
    width: inherit;
    display: flex;
    flex-direction: row;
  }
</style>