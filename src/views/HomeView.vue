<template>
  <div class="home">
    <HeaderComponent :randomPokemon="item"/>
    <PokemonComponent :pokemons="pokemonObject" :flatPokemons="tempArr" @selectPokemon="selectPokemon" />
    <FooterComponent @randomizer="randomize"/>
  </div>
</template>

<script>
// @ is an alias to /src
import pokemon from '@/data/pokemon.json'
import HeaderComponent from '@/components/HeaderComponent.vue'
import PokemonComponent from '@/components/PokemonComponent.vue'
import FooterComponent from '@/components/FooterComponent.vue'

import { ref } from '@vue/reactivity'

export default {
  name: 'HomeView',
  components: {
  HeaderComponent,
  PokemonComponent,
  FooterComponent    
  },
  setup() {
    const pokemonObject = ref(pokemon)

    const tempArr = ref([])
    for(let pokemonType in pokemonObject.value)
    {
      pokemonObject.value[pokemonType].forEach((val) => {
        tempArr.value.push(val)
      })      
    }

    const item = ref(tempArr.value[Math.floor(Math.random()*tempArr.value.length)])

    const selectPokemon = ((poke) => {
      item.value = poke
    })

    const randomize = (() => {
      item.value = tempArr.value[Math.floor(Math.random()*tempArr.value.length)]
    })

    return {
      item,
      pokemonObject,
      tempArr,
      selectPokemon,
      randomize
    }
  }
}
</script>
