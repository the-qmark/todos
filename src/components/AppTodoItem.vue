<template>
  <li
    class="todo-item "
    :class="{ 'todo-item--done': todo.completed }"
  >
    <div class="todo-item__status">
      <i class="bi bi-check2"></i>
    </div>
    <span class="todo-item__text">{{ todo.text }}</span>
    <button class="todo-item__remove-button">
      <i class="bi bi-trash3"></i>
    </button>
  </li>
</template>

<script setup lang="ts">
import { defineProps, PropType } from 'vue';
import { Todo } from '@/types/Todo'


const props = defineProps({
  todo: {
    type: Object as PropType<Todo>,
    required: true
  }
})

</script>