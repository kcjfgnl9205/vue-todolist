<script setup lang="ts">
interface Props {
  title: string;
}

defineProps<Props>();
</script>

<template>
  <h1 class="mt-12 text-2xl font-semibold">{{ title }}</h1>
</template>
