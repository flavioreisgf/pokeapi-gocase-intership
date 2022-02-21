<template>
<div>
    <h1>{{ titulo }}</h1>
    <ul>
        <li v-for="pokemon in pokemons.results" :key="pokemon.name">{{pokemon.name}} {{pokemon.url}}</li>
    </ul>
</div>
</template>

<script setup>

const titulo = "Lista de Pokemons"

const listPokemon = await fetch('https://pokeapi.co/api/v2/pokemon/')
const pokemons = await listPokemon.json()


</script>

<style>

</style>