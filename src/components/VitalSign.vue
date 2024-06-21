<template>
    <div :class="wrapperClass">
      <component :is="icon" class="mb-2 h-[96px] w-[96px]"></component>
      <p class="text-[16px]">{{ title }}</p>
      <p class="text-3xl font-extrabold">{{ value }}</p>
      <div class="flex items-center gap-2">
        <img v-if="levels === 'Higher than Average'" src="../assets/ArrowUp.svg" alt="Higher" class="w-[10px] h-[5.48px]">
        <img v-if="levels === 'Lower than Average'" src="../assets/ArrowDown.svg" alt="Lower" class="w-[10px] h-[5.48px]">
        <p class="text-[16px] pt-2">{{ levels }}</p>
      </div>
    </div>
</template>
  
<script setup>
  import { defineProps } from 'vue';
  
  const props = defineProps({
    icon: String,
    title: String,
    value: String,
    levels: String,
    wrapperClass: String,
  });
</script>  