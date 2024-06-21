<template>
    <div>
      <div :class="borderClass">
        <div class="flex items-center gap-1">
          <div :class="roundedClass"></div>
          <p class="text-[#072635] font-bold">{{ label }}</p>
        </div>
        <p class="text-[22px] font-bold">{{ value }}</p>
        <div class="flex items-center gap-2">
          <component v-if="levels === 'Higher than Average'" :is="ArrowUpIcon" class="w-[10px] h-[5.48px]"></component>
          <component v-if="levels === 'Lower than Average'" :is="ArrowDownIcon" class="w-[10px] h-[5.48px]"></component>
          <p class="text-[#072635] text-[14px]">{{ levels }}</p>
        </div>
      </div>
    </div>
</template>
  
<script setup>
  import { defineProps, computed } from 'vue';
  import ArrowUpIcon from '../components/icons/ArrowUp.vue';
  import ArrowDownIcon from '../components/icons/ArrowDown.vue';
  
  const props = defineProps({
    label: String,
    value: String,
    levels: String,
    color: String,
    isBorderBottom: Boolean
  });
  
  const borderClass = computed(() => {
    return props.isBorderBottom ? 'border-b-[1.5px] border-gray-300 pb-4 pr-16' : 'pt-4';
  });
  
  const roundedClass = computed(() => {
    return `rounded-full ${props.color} w-[14px] h-[14px]`;
  });
</script>