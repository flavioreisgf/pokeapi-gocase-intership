<template>
<div class="caixa">
    <h1 class="centralizado"><img class="logo" src="https://i2.wp.com/multarte.com.br/wp-content/uploads/2019/03/pokemon-png-logo.png?fit=2000%2C736&ssl=1" alt="Logo Pokemon sem fundo"></h1>
    <div class="search-title">
    </div>


    <ul>
        <li v-for="pokemon in listSearch" :key="pokemon.name"><a :href="'pokemon/' + pokemon.name">{{pokemon.name}}</a></li>
    </ul>
</div>
</template>

<script setup>

import {ref, watch} from "vue"


const search = ref("")

const listPokemon = await fetch('https://pokeapi.co/api/v2/pokemon/?limit=1126')
const pokemons = await listPokemon.json()

let listSearch = pokemons.results



</script>

<style>
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

.search-title{
    position: relative;
}

.search{
    padding: 4px 12px;
    color: black;
    border: 1px solid black;
    background: white;
    width: 400px;
}

.enviar{
    margin-left: 5px;
    padding: 3px 12px;
}


.logo{
    width: 60%;
}

li{
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
li:hover {
    transform:scale(1.2);
    border: none;
    color: yellow;
}
</style>