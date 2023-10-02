<template>
  <ul class="todo-list">
    <AppTodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggle-todo="onToggleTodo"
      @delete-todo="onDeleteTodo"
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

const onToggleTodo = (id: number) => {
  const targetTodo = todos.value.find((todo: ITodo) => todo.id === id)

  if (targetTodo) {
    targetTodo.completed = !targetTodo.completed
  }
}

const onDeleteTodo = (id: number) => {
  const targetTodo = todos.value.find((todo: ITodo) => todo.id === id)

  if (targetTodo) {
    todos.value = todos.value.filter((todo: ITodo) => todo.id != id)
  }
}

</script>