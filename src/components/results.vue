<template>
  <h1 v-if="score <= 100">Extremely fast</h1>
  <h1 v-else-if="score >100 && score <= 300">fast</h1>
  <h1 v-else-if="score >300 && score <= 500">normal</h1>
  <h1 v-else-if="score >500">slow</h1>
  
</template>

<script setup>

   const props = defineProps({
        score: Number,
    })

</script>

<style>

</style>