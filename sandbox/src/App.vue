<script>
// https://pokeapi.co/api/v2/pokemon?limit=151

export default {
  data : () => ({
    pokedex : [1,2,3]
  }),
  methods : {
    async fetchPokemon () {
      this.pokedex = await fetch('https://pokeapi.co/api/v2/pokemon?limit=151').then(response => response.json())
    }
  },
  beforeCreate () {
    console.log('Hello')
    console.log(this.pokedex)
  },
  created() {
    console.log('2nd hello')
    this.fetchPokemon()
  },
}

</script>

<template>
  <h1>New app</h1>
  <pre>
    {{ pokedex }}
  </pre>
  <button @click="fetchPokemon">Fetch pokemon</button>
</template> 