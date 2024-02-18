<script setup lang="ts">
import { ref } from 'vue';
import Header from './components/Header.vue';
import Empty from './components/Empty.vue';
import Button from './components/Button.vue';
import TodoComponent from './components/Todo.vue';
import InputText from './components/InputText.vue';
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
    <Header title="TODO LIST" />

    <form
      @submit.prevent="addTodo"
      class="flex w-full h-12 gap-4 border-neutral-100 border-[1px]"
    >
      <InputText v-model="todo" placeholder="todo" type="text" />
      <Button type="submit" title="추가" />
    </form>

    <div v-if="todos.length === 0" class="mx-auto text-xl font-semibold">
      <Empty msg="TODO LIST가 존재하지 않습니다." />
    </div>
    <div v-else>
      <ul class="flex flex-col gap-2">
        <TodoComponent
          v-for="todo in todos"
          :key="todo.date.toString()"
          :todo="todo"
          @remove="removeTodo"
        />
      </ul>
    </div>
  </main>
</template>
