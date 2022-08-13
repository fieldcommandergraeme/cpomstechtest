<template>
  <img :src="randomPokemon.image">
  <h3>Name: {{randomPokemon.name}}</h3>
  <h3>Classification: {{randomPokemon.name}}</h3>
</template>

<script>

export default {
props: {
    randomPokemon: Object
},
setup () {

}
}
</script>

<style>

</style>