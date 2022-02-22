<template>
  <div class="caixa">
  <h1>The Pokemon is {{pokemon.name}}</h1>
  <img :src="pokemon.sprites.front_default" alt="Pokemon Image">
  <p class="weight">The weight of {{pokemon.name}} is {{pokemon.weight}}</p>
  <p class="height">The height of {{pokemon.name}} is {{pokemon.height}}</p>
  <ul>
    <p>Abilities</p>
    <li class="lista-abilities" v-for="ability in pokemon.abilities" :key="ability.ability.name">
      {{ability.ability.name}}
    </li>
  </ul>
  </div>
</template>

<script setup>

const router = useRoute();

const url = 'https://pokeapi.co/api/v2/pokemon/' + router.params.name;
const results = await fetch(url);
const pokemon = await results.json();

</script>

<style scoped>

h1, p {
  text-transform: capitalize;
}

.caixa{
    background: rgba(248, 227, 227, 0.452);
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
}
.lista-abilities {
    display: inline-block;
    text-align: center;
    width: 100%;
    margin: 1% auto;
    padding: 30px 20px;
    box-sizing: border-box;
    border: solid 2px black;
    border-radius: 10px;
    font-weight: bold;
    text-transform: uppercase;
    transition: 500ms;
}

li:hover {
    transform:scale(1.2);
    color: yellow;
}
</style>