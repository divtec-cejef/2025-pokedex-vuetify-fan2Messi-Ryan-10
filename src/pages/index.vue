<template>
  <v-container>
    <h1 class="mb-6 text-center">Pokédex</h1>

    <v-text-field
      v-model="search"
      clearable
      label="Rechercher un Pokémon"
      prepend-icon="mdi-magnify"
    />
    <v-col
      v-for="pokemon in filteredPokemons"
      :key="pokemon.id"
      cols="12"
      lg="3"
      md="4"
      sm="6"
      xl="2"
    >
      <PokemonCard :pokemon="pokemon" />
    </v-col>
    <v-alert v-if="filteredPokemons.length === 0" class="text-center mt-4" type="warning">
      Aucun Pokémon ne correspond à votre recherche.
    </v-alert>
  </v-container>
</template>
<script setup>
  import { usePokemonStore } from '@/stores/pokemonStore'
  import { computed, ref } from 'vue'
  const pokemonStore = usePokemonStore()
  console.log(pokemonStore.pokemons)
  const search = ref('')
  const filteredPokemons = computed(() => {
    const query = search.value.toLowerCase().trim()
    return sortedPokemons.value.filter(pokemon =>
      pokemon.name.toLowerCase().includes(query)
    )
  })
  const sortDirection = ref('asc')
  const sortedPokemons = computed(() => {
    return [...pokemonStore.pokemons].sort((a, b) =>
      sortDirection.value === 'asc'
        ? a.name.localeCompare(b.name)
        : b.name.localeCompare(a.name)
    )
  })
</script>
