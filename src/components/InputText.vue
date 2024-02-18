<script setup lang="ts">
interface Props {
  type: string;
  placeholder: string;
}

const model = defineModel();

defineProps<Props>();
defineEmits(['update:modelValue']);
</script>

<template>
  <input
    :type="type"
    :placeholder="placeholder"
    v-model="model"
    class="w-full border-[1px] border-indigo-500 rounded-lg px-4"
  />
</template>
