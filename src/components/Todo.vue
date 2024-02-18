<script setup lang="ts">
import { Todo } from '../types';

interface Props {
  todo: Todo;
}

defineProps<Props>();
defineEmits<{
  (e: 'remove', todo: Todo): void;
}>();
</script>

<template>
  <li
    class="flex gap-2 w-full justify-between border-[1px] border-neutral-200 px-4 py-2 hover:bg-neutral-100 rounded-lg"
  >
    <p class="">{{ todo.text }}</p>
    <button
      @click="$emit('remove', todo)"
      class="flex w-[32px] h-[32px] justify-center items-center bg-rose-500 text-white rounded-lg text-sm p-2"
    >
      X
    </button>
  </li>
</template>
