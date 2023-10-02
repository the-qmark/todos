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
import { PropType, ref } from 'vue';
import AppTodoItem from './AppTodoItem.vue'
import { ITodo } from '@/types/Todo';


const props = defineProps({
  todos: Array as PropType<ITodo[]>
})

const emits = defineEmits({
  'toggle-todo': (id: number) => Number.isInteger(id),
  'delete-todo': (id: number) => Number.isInteger(id)
})

const onToggleTodo = (id: number) => {
  emits('toggle-todo', id);
}

const onDeleteTodo = (id: number) => {
  emits('delete-todo', id);
}
</script>