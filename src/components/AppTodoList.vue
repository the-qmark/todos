<template>
  <ul class="todo-list">
    <AppTodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
    />
  </ul>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import AppTodoItem from './AppTodoItem.vue'
import { ITodo } from '@/types/Todo';

const todos = ref<ITodo[]>([
  {
    id: 0,
    text: 'Text 11111',
    completed: true
  },
  {
    id: 1,
    text: 'Text 2222',
    completed: false
  },
])

</script>