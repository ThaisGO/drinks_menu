<script setup>
  import drinks from './data/db.json'
  import DrinkCard from './components/DrinkCard.vue';
</script>

<template>
  <div class="border-5 border-solid border-orange-500 rounded-lg m-3 py-3">
    <header>
      <h1 class="text-4xl text-center font-bold uppercase underline text-orange-500 mb-3">Cardápio</h1>
    </header>
  
    <main class="px-5 flex flex-col">
      <DrinkCard v-for="drink in drinks" :key="drink.id" :drink="drink" />
    </main>

  </div>
</template>
