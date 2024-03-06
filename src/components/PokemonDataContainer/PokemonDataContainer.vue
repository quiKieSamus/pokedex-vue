<script setup>
defineProps(['data']);

const notFoundSource = "https://static.vecteezy.com/system/resources/previews/005/337/799/non_2x/icon-image-not-found-free-vector.jpg";

</script>

<template>
    <div>
        <div class="img">
            <img height="96" width="96
            " v-bind:src="data?.sprites?.front_default ?? notFoundSource" v-bind:alt="`Imagen de ${data?.name}`">
        </div>
        <div class="title">
            {{ data?.name ?? "No se encontró" }}
        </div>
        <div class="">

        </div>
    </div>
</template>