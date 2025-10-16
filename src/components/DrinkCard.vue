<script setup>
import { ref } from 'vue'

const props = defineProps({
   drink: Object
})

const loaded = ref(false)

const getClass = (tag) => {
   switch (tag) {
      case "com-alcool": return "bg-orange-500"
      case "sem-alcool": return "bg-blue-950"
      default: return "bg-gray-300"
   }
}
</script>

<template>
   <div class="flex gap-5 mb-10">
      <div class="relative">
         <!-- Imagem -->
         <div v-if="!loaded" class="absolute inset-0 bg-gray-200 animate-pulse rounded-lg"></div>
         
         <img 
            :src="drink.image"
            :alt="drink.name"
            loading="lazy"
            @load="loaded = true"
            class="w-[100px] max-w-xs rounded-lg transition-opacity duration-500"
            :class="loaded ? 'opacity-100' : 'opacity-0'"
         />
      </div>

      <!-- Conteúdo -->
      <div class="flex flex-col gap-2">
         <h2 class="text-xl underline font-bold text-orange-500">{{ drink.name }}</h2>
         <p class="text-base">{{ drink.description }}</p>
         <div class="flex gap-2 mt-2 flex-wrap">
            <span 
               v-for="tag in drink.tags" 
               :key="tag"
               class="text-xs text-white font-bold py-1 px-2 rounded"
               :class="getClass(tag)"
            >
               {{ tag.replace('-', ' ') }}
            </span>
         </div>
      </div>
   </div>
</template>
