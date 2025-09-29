<template>
  <v-container>
    <h1 class="mb-6 text-center">Pokédex</h1>

    <v-text-field
      clearable
      label="Rechercher un Pokémon"
      prepend-icon="mdi-magnify"
    />
    <v-col
      v-for="pokemon in pokemonStore.pokemons"
      :key="pokemon.id"
      cols="12"
      lg="3"
      md="4"
      sm="6"
      xl="2"
    >
      <PokemonCard :pokemon="pokemon" />
    </v-col>
  </v-container>
</template>
<script setup>
  import { usePokemonStore } from '@/stores/pokemonStore'
  const pokemonStore = usePokemonStore()
  console.log(pokemonStore.pokemons)
</script>
