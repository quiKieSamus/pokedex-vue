<script setup>
// component prop, data is an object which receives the data from pokeapi
defineProps(['data']);

const notFoundImageSource = "https://static.vecteezy.com/system/resources/previews/005/337/799/non_2x/icon-image-not-found-free-vector.jpg";

</script>

<template>
    <div>
        <div class="img">
            <img height="96" width="96" v-bind:src="data?.sprites?.front_default ?? notFoundImageSource"
                v-bind:alt="`Imagen de ${data?.name ?? `Loading...`}`">
        </div>
        <div class="name">
            {{ data?.name ?? "No se encontró" }}
        </div>
        <div class="types">
            <span v-for="types in data?.types">
                {{ types?.type?.name ?? "N/A" }}
            </span>
        </div>
        <div class="stats">

        </div>
        <div class="desc">
            {{ `hola`  }}
        </div>
    </div>
</template>