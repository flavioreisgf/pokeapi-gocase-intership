<template>
  <div class="container">
    <header> <h1>The Pokemon is {{pokemon.name}}</h1> </header>
    <main> 
        <div class="caixa">
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
    </main>
    <footer> 
      <p><a href="https://github.com/flavioreisgf/pokeapi-gocase-intership"> Github Project </a></p> 
      <button class="button" type="button" onclick="javascript:history.back()">Back</button>
    </footer>
  </div>

</template>

<script setup>

const router = useRoute();

const url = 'https://pokeapi.co/api/v2/pokemon/' + router.params.name;
const results = await fetch(url);
const pokemon = await results.json();

</script>

<style scoped>
.container{
  height: 100vh;
}

h1, p {
  text-transform: capitalize;
}

.caixa{
    background: rgba(248, 227, 227, 0.452);
    width: 100%;
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
    background:rgba(194, 46, 46, 0.452) ;

}

li:hover {
    transform:scale(1.2);
    color: yellow;
}

a{
    text-decoration: none;
    color: black;
}

a:hover {
    color: yellow;
    transform: scale(1.2);
    text-decoration: underline;
}

header, footer{
    background: rgba(194, 46, 46, 0.452);
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    text-transform: uppercase;
}

.button {
  background-color: #c43636;
  border: none;
  color: white;
  padding: 10px 24px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 12px;
  margin-bottom: 1em;
  transition-duration: 0.4s;
  cursor: pointer;
}

.button:hover{
    background-color: white; 
    color: #c43636;
}

@media screen and (max-width: 540px) {
    .caixa {
        width: auto;
    }
    h1, p{
        text-align: center;
    }

    .lista-abilities{
        width: 90%;
        margin-right: 10px;
        text-align: center;
    }
}

</style>