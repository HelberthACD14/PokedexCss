<script setup lang="ts">
import axios from 'axios';
import Pokemon from './components/Pokemon.vue';
import { onBeforeMount, ref } from 'vue';

const pokemons = ref();

onBeforeMount(async ()=> {
  try {
    const response = await axios.get('https://pokeapi.co/api/v2/pokemon?limit=151');
    pokemons.value = response.data.results;
  } catch (error) {
    console.error('Error al obtener la lista de pokémon:', error);
  }
})


</script>

<template>
  <h1>
    Pokedex for MyTP
  </h1>
  <div class="wrapper">
    <div  v-for="(pokemon, index) in pokemons" class="sonPokemon" :key="index">    
      <Pokemon :url="pokemon.url"></Pokemon>
    </div>
  </div>
</template>

<style lang="scss">
body{
  background: repeating-linear-gradient(#007810, #007810 40px, #36B24B 40px, #36B24B 80px);
  font-family: "Press Start 2P";
}
h1{
  background-color: #ddd;
  border: 10px double;
  padding: 10px 30px;//10px 30px 5px 25px -- 10px 30px -- 10px
}
.wrapper{
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  column-gap: 10px;
  row-gap: 10px;
}

.sonPokemon:nth-child(odd){
  background-color: #99b;
  border: 5px double;
  padding: 5px 5px;
}
.sonPokemon:nth-child(even){
  background-color: #dda;
  border: 5px double;
  padding: 10px 10px;
}

</style>