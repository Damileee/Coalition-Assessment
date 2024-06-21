<template>
    <div class="rounded-2xl bg-white py-2 pr-4">
      <h3 class="text-xl pl-6 pt-2 font-bold mb-0">Lab Results</h3>
      <div class="py-4 pl-6 w-full">
        <ul class="space-y-2 overflow-y-auto max-h-48">
          <li v-for="(result, index) in labResults" :key="index" class="flex justify-between items-center py-2 pl-3 pr-4 hover:bg-gray-100 rounded-sm">
            <span class="font-medium">{{ result }}</span>
            <img src="../assets/downloadIcon.svg" alt="Download" class="w-5 h-5 cursor-pointer" />
          </li>
        </ul>
      </div>
    </div>
</template>
  
<script setup>
  import { defineProps } from 'vue';
  
  const props = defineProps({
    labResults: {
      type: Array,
      required: true,
    },
  });
</script>
  
<style scoped>
  .overflow-y-auto {
    overflow-y: auto;
  }
  
  .overflow-y-auto::-webkit-scrollbar {
    width: 6px;
  }
  
  .overflow-y-auto::-webkit-scrollbar-track {
    background: #f1f1f1;
    border-radius: 10px;
  }
  
  .overflow-y-auto::-webkit-scrollbar-thumb {
    background: #888;
    border-radius: 10px;
  }
  
  .overflow-y-auto::-webkit-scrollbar-thumb:hover {
    background: #555;
  }
</style>  