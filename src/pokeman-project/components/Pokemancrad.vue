<template>
  <div class="cards">
   
    <card 
      v-for="p in pokemons" 
      :key="p.id" 
      class="card"
     @click="clickFun(p)"
     :class="{opace:selectedId && p.id !== selectedId}"
    >
     <template v-slot:title>
        {{ p.name }} #{{ p.id }}
      </template>

      <template v-slot:content>
        <img :src="p.sprite" />
      </template>

      <template v-slot:description>
        <div v-for="type in p.types" :key="type.name">
          {{ type.name }}
        </div>
      </template>
    </card>
  </div>
</template>

<script>
 //Vue slots are a fantastic way to inject content from a parent component
 // into a child component.
import Card from './Card.vue'
export default {
    components: {
    Card
  },
  props:{
    pokemons:Array,
     selectedId: {
      type: Number
    }
  },
  
   
  methods: {
    clickFun(pokemon) {
      console.log("hii")
      this.$emit('pokemonSelected', pokemon)
    }
  }
}
</script>

<style scoped>
img {
  width: 100%;
}
.cards {
  display: flex;
  justify-content: center;
  margin-top: 15px;
}
.opace {
  opacity: 0.5;
}
.card:hover {
  opacity: 1;
}
</style>