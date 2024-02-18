<script setup lang="ts">
interface Props {
  msg?: string;
}

const { msg } = withDefaults(defineProps<Props>(), {
  msg: '데이터가 존재하지 않습니다.',
});
</script>

<template>
  <h1 class="mt-12 text-2xl font-semibold">
    {{ msg }}
  </h1>
</template>
