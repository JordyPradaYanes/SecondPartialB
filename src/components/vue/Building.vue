<script setup>
import { ref, computed } from "vue";

const board = ref("");

const wordCount = computed(() => board.value.split(' ').filter(word => word !== '').length);

const bar1Class = computed(() => ({
  'bg-red-600': wordCount.value >= 1
}));
const bar2Class = computed(() => ({
  'bg-orange-600': wordCount.value >= 3
}));
const bar3Class = computed(() => ({
  'bg-yellow-600': wordCount.value >= 5
}));
const bar4Class = computed(() => ({
  'bg-green-600': wordCount.value >= 7
}));
</script>

<template>
  <section class="w-full flex flex-col items-center justify-center">
    <div class="flex flex-row items-end">
      <div class="bg-gray-400 w-4 h-8 m-5" :class="bar1Class"></div>
      <div class="bg-gray-400 w-4 h-16 m-5" :class="bar2Class"></div>
      <div class="bg-gray-400 w-4 h-28 m-5" :class="bar3Class"></div>
      <div class="bg-gray-400 w-4 h-40 m-5" :class="bar4Class"></div>
    </div>
    <input type="text" class="bg-blue-950 text-white p-2" v-model="board">
  </section>
</template>