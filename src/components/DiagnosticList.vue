<template>
    <div class="bg-white rounded-2xl p-6 w-full h-[300px]">
      <h3 class="text-xl font-bold mb-2">Diagnostic List</h3>
      <div class="relative overflow-hidden">
        <table class="w-full table-auto">
          <thead class="bg-gray-100 mb-2">
            <tr>
              <th class="px-4 py-2 text-left w-1/3 rounded-l-full">Problem/Diagnosis</th>
              <th class="px-4 py-2 text-left w-1/3">Description</th>
              <th class="px-4 py-2 text-left w-1/3 rounded-r-full">Status</th>
            </tr>
          </thead>
        </table>
        <div class="overflow-y-auto py-2 mt-2 max-h-40">
          <table class="w-full table-auto">
            <tbody>
              <tr v-for="(diagnostic, index) in diagnosticList" :key="index" class="hover:bg-gray-50">
                <td class="border-b px-4 py-3 w-1/3">{{ diagnostic.name }}</td>
                <td class="border-b px-4 py-3 w-1/3">{{ diagnostic.description }}</td>
                <td class="border-b px-4 py-3 w-1/3">{{ diagnostic.status }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
</template>
  
<script setup>
  import { defineProps } from 'vue';
  
  const props = defineProps({
    diagnosticList: {
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
  