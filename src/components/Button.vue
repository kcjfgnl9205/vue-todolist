<script setup lang="ts">
interface Props {
  title: string;
}

defineProps<Props>();
</script>

<template>
  <button
    class="flex w-[50px] justify-center items-center bg-indigo-500 text-white rounded-lg"
  >
    {{ title }}
  </button>
</template>
