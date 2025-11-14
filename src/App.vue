<script setup lang="ts">
  import { ref } from 'vue';
  import MainStoryContent from './contents/MainStoryContent.vue';
  import BondStoryContent from './contents/BondStoryContent.vue';

  const currentView = ref('main');

  const setActiveView = (view: string) => {
    currentView.value = view;
    console.log('Current View:', currentView.value);
  };
</script>

<template>
  <div class="text-white">
    <div class="flex flex-col items-center bg-gray-800 p-4 rounded-t-md gap-4">
      <text class="text-6xl font-bold">Niya Archive</text>
      
      <div class="flex gap-8 w-full justify-center border-t border-gray-700 pt-4"> 

        <button 
          @click="setActiveView('main')"
          :class="{ 
            'bg-indigo-600 hover:bg-indigo-700 shadow-2xl': currentView !== 'main', 
            'bg-yellow-500 text-gray-900 shadow-yellow-500/50 scale-105': currentView === 'main' 
          }"
          class="p-6 text-xl rounded-xl font-bold transition duration-150 ease-in-out transform"
        >
          Main Story
        </button>

        <button 
          @click="setActiveView('bond')"
          :class="{ 
            'bg-teal-600 hover:bg-teal-700 shadow-2xl': currentView !== 'bond', 
            'bg-yellow-500 text-gray-900 shadow-yellow-500/50 scale-105': currentView === 'bond' 
          }"
          class="p-6 text-xl rounded-xl font-bold transition duration-150 ease-in-out transform"
        >
          Bond Story
        </button>
      </div>
    </div>
    
    <div class="bg-gray-800 p-4 rounded-b-md">
      <hr class="border-gray-700 my-4" />
      
      <MainStoryContent v-if="currentView === 'main'" />
      <BondStoryContent v-else />
      
    </div>
  </div>
</template>