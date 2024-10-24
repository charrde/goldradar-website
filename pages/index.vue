<template>
  <div>
    <h1 class="text-3xl font-bold mb-4">Gold Mines in Canada</h1>
    <client-only>
      <GoldMinesMap />
    </client-only>
  </div>
</template>

<script setup lang="ts">
// Import the GoldMinesMap component
import GoldMinesMap from '~/components/Map.vue'
</script>

<style scoped>
</style>
