<template>
  <v-card class="pt-4">
    <v-img contain height="200" :src="`/images/${pokemon.img}`" />
    <v-card-title>{{ pokemon.name }}</v-card-title>
    <v-card-subtitle>
      <v-card-text>Level: {{ pokemon.level }}</v-card-text>
    </v-card-subtitle>
    <v-btn
      icon
      variant="plain"
      class="position-absolute top-0 right-0 mt-2 mr-2"
      @click.prevent="pokemonStore.toggleFavorite(pokemon)"
    >
      <v-icon :color="pokemonStore.isFavorite(pokemon) ? 'red' : ''">
        {{ pokemonStore.isFavorite(pokemon) ? 'mdi-heart' : 'mdi-heart-outline' }}
      </v-icon>
    </v-btn>
    <!-- À compléter plus tard avec les types -->
  </v-card>
</template>

<script setup>
  import { usePokemonStore } from '@/stores/pokemonStore'
  const pokemonStore = usePokemonStore()
  defineProps({
    pokemon: Object,
  })
</script>
