<script setup lang="ts">
import { ref } from 'vue';
import { Todo } from './types';

const todo = ref('');
const todos = ref<Todo[]>([]);

const addTodo = () => {
  if (todo.value === '') return;

  todos.value.push({ text: todo.value, date: new Date(), done: false });
  todo.value = '';
};

const removeTodo = (todo: Todo) => {
  todos.value = todos.value.filter((item) => item !== todo);
};
</script>

<template>
  <main class="mx-auto w-full sm:w-[758px] flex flex-col gap-4 px-2">
    <h1 class="mt-12 text-2xl font-semibold">TODO LIST</h1>

    <form
      @submit.prevent="addTodo"
      class="flex w-full h-12 gap-4 border-neutral-100 border-[1px]"
    >
      <input
        v-model="todo"
        class="w-full border-[1px] border-indigo-500 rounded-lg px-4"
      />
      <button
        type="submit"
        class="flex w-[50px] justify-center items-center bg-indigo-500 text-white rounded-lg"
      >
        추가
      </button>
    </form>

    <div v-if="todos.length === 0" class="mx-auto text-xl font-semibold">
      데이터가 없음
    </div>
    <div v-else>
      <ul class="flex flex-col gap-2">
        <li
          v-for="todo in todos"
          :key="todo.date.toString()"
          class="flex gap-2 w-full justify-between border-[1px] border-neutral-200 px-4 py-2 hover:bg-neutral-100 rounded-lg"
        >
          <p class="">{{ todo.text }}</p>
          <button
            @click="removeTodo(todo)"
            class="flex w-[32px] h-[32px] justify-center items-center bg-rose-500 text-white rounded-lg text-sm p-2"
          >
            X
          </button>
        </li>
      </ul>
    </div>
  </main>
</template>
