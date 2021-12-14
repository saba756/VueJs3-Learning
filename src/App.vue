<template>
<div>
  <PokemonCards
     :pokemons="pokemons" 
    :selectedId="selectedId"
    @pokemonSelected="fetchEvolutions"
  />
   <PokemonCards :pokemons="evolutions" />
</div>
</template>

<script>

import PokemonCards from './pokeman-project/components/Pokemancrad.vue'
const api='https://pokeapi.co/api/v2/pokemon'
const IDS=[1,4,7]
export default {
    components: {
    PokemonCards
  },
  data(){
    return {
      pokemons:[],
      evolutions:[],
      selectedId: null
    }
  },
  async created(){
this.pokemons=  await  this.fetchData(IDS)
  },
methods:{
    async fetchEvolutions(pokemon) {
      console.log("pokemon",pokemon)
      this.evolutions = await this.fetchData(
        [pokemon.id + 1, pokemon.id + 2]
      )
      this.selectedId = pokemon.id
    },
  async fetchData(ids){
const response =  await  Promise.all(ids.map(id => window.fetch(`${api}/${id}`)));
const jsondata= await Promise.all(response.map(data => data.json()))

return jsondata.map(data=>({
  id: data.id,
   name: data.name,
  sprite: data.sprites.other['official-artwork'].front_default,
  types: data.types.map(type => {
          return {
            name: type.type.name
          }
        })
})

)

  }
}
}
</script>

<style scoped>

</style>