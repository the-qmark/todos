<template>
  <li
    class="todo-item "
    :class="{ 'todo-item--done': todo.completed }"
    @click="toggleTodo"
  >
    <div class="todo-item__status">
      <i class="bi bi-check2"></i>
    </div>
    <span class="todo-item__text">{{ todo.text }}</span>
    <button
      class="todo-item__remove-button"
      @click.stop="deleteTodo"
    >
      <i class="bi bi-trash3"></i>
    </button>
  </li>
</template>

<script setup lang="ts">
import { defineEmits, defineProps, PropType } from 'vue';
import { ITodo } from '@/types/Todo'

const props = defineProps({
  todo: {
    type: Object as PropType<ITodo>,
    required: true
  }
})

const emits = defineEmits({
  'toggle-todo': (id: number) => Number.isInteger(id),
  'delete-todo': (id: number) => Number.isInteger(id)
})

const toggleTodo = () => {
  emits('toggle-todo', props.todo.id);
}

const deleteTodo = () => {
  emits('delete-todo', props.todo.id);
}

</script>