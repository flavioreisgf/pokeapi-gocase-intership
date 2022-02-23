<template>
    <header><h1 class="centralizado"><img class="logo" src="https://i2.wp.com/multarte.com.br/wp-content/uploads/2019/03/pokemon-png-logo.png?fit=2000%2C736&ssl=1" alt="Logo Pokemon sem fundo"></h1></header>
    <main>
        <div class="caixa">
            
            <ul>
                <li class="listaPoke" v-for="pokemon in listSearch" :key="pokemon.name"><a :href="'pokemon/' + pokemon.name"><img src="https://www.pinpng.com/pngs/m/8-82850_poke-ball-png-pokeball-png-transparent-png.png" width="20px" height="20px" alt="pokebola"> {{pokemon.name}}</a></li>
            </ul>
    </div>
    </main>

    <footer> <a href="https://github.com/flavioreisgf/pokeapi-gocase-intership"> Github Project </a> </footer>
</template>

<script setup>
import { ref } from 'vue';

/*Another way of getting the API data
let listSearch = ref([])

fetch('https://pokeapi.co/api/v2/pokemon/?limit=1126')
    .then((listPokemon) => listPokemon.json())
    .then((response) => listSearch.value = response.results) */


const listPokemon = await fetch('https://pokeapi.co/api/v2/pokemon/?limit=1126')
const pokemons = await listPokemon.json()

let listSearch = pokemons.results

</script>

<style scoped>
.caixa{
    background: rgba(248, 227, 227, 0.452);
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
}
.centralizado{
    text-align: center;
}

.logo{
    width: 60%;
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

.listaPoke{
    display: inline-block;
    text-align: center;
    width: 22%;
    margin: 1% 1%;
    padding: 30px 20px;
    box-sizing: border-box;
    border: solid 2px black;
    border-radius: 10px;
    font-weight: bold;
    text-transform: uppercase;
    transition: 500ms;
}   
.listaPoke:hover {
    transform:scale(1.2);
}

footer, header{
     background: rgba(248, 227, 227, 0.452);
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    text-transform: uppercase;
}

@media screen and (max-width: 540px) {
    .caixa {
        width: auto;
    }
    .centralizado{
        text-align: center;
    }

    .listaPoke{
        width: 90%;
        margin-right: 10px;
        text-align: center;
    }
}

</style>