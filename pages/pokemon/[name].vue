<template>
      <h1>The Pokemon is {{pokemon.name}}</h1>
  <img :src="pokemon.sprites.front_default" alt="Pokemon Image">
  <p class="weight">The weight of {{pokemon.name}} is {{pokemon.weight}}</p>
  Abilities:
  <ul>
    <li v-for="ability in pokemon.abilities" :key="ability.ability.name">
      {{ability.ability.name}}
    </li>
  </ul>
</template>
<script setup>

const router = useRoute();


const url = 'https://pokeapi.co/api/v2/pokemon/' + router.params.name;
const results = await fetch(url);
const pokemon = await results.json();

</script>

<style>
</style>