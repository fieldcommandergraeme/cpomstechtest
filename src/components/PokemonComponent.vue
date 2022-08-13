<template>
	<label for="pokemonType">Choose a Type:</label>
	<br/>
  <select name="pokemonType" id="pokemonType" @change="filterPokemons(type)" v-model="type">
  <option v-for="type in typeArray" :value="type" :key="type">{{type}}</option>
	</select>

	<div class="scroll">
	<div v-for="pokemon in pokemonArray" :key="pokemon">
		<div class="pokemon" @click="selectedPokemon(pokemon)">
			{{pokemon.name}}
		</div>
	</div>
	</div>
</template>

<script>
import { ref } from '@vue/reactivity'
export default {
props: {
    pokemons: Object,
		flatPokemons: Object
},
emits: ['selectPokemon'],
setup (props, {emit}) {
	const typeArray = ref([])
	const pokemonArray = ref(props.flatPokemons)
	for(let type in props.pokemons)
	{
		typeArray.value.push(type)
	}

	const filterPokemons = ((typeOfPokemon) => {
		pokemonArray.value = props.pokemons[typeOfPokemon]
	})

	const selectedPokemon = ((pokemon) => {
		emit('selectPokemon', pokemon)
	})

	return {typeArray, filterPokemons, pokemonArray, selectedPokemon}
}
}
</script>

<style>
.pokemon {
	border: solid 1px black;
	padding:10px;
	margin:10px;
	cursor: "pointer";
	text-align: "center"
}

.scroll {
    padding: 4px;
    width: 100%;
    height: 550px;
    overflow-x: hidden;
    overflow-y: auto;
    text-align: justify;
}
</style>