<template>
  <v-card class="pt-4">
    <v-img contain height="200" :src="`/images/${pokemon.img}`" />
    <v-card-title>{{ pokemon.name }}</v-card-title>
    <v-card-subtitle>
      <v-card-text>Level: {{ pokemon.level }}</v-card-text>
    </v-card-subtitle>
    <!-- À compléter plus tard avec les types -->
  </v-card>
</template>

<script setup>
  defineProps({
    pokemon: Object,
  })
</script>
