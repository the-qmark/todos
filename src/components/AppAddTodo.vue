<template>
  <section class="add-todo">
    <form
      v-if='isFormVisible'
      class="add-todo__form"
      @submit.prevent="addTodo"
    >
      <button
        class="close-button"
        type="button"
        @click="closeForm"
      >
        <i class="bi bi-x"></i>
      </button>
      <div class="text-input text-input--focus">
        <input
          ref="input"
          v-model="todoText"
          class="input"
        />
      </div>
      <button class="button button--filled">Add task</button>
    </form>
    <button
      v-else
      class="add-todo__show-form-button"
      @click="showForm"
    >
      <i class="bi bi-plus-lg"></i>
    </button>
  </section>
</template>

<script setup lang="ts">
import { ITodo } from '@/types/Todo';
import { nextTick, ref } from 'vue';

const isFormVisible = ref<boolean>(false)

const input = ref<HTMLInputElement | null>(null)
const showForm = () => {
  isFormVisible.value = true
  nextTick(() => {
    if (input.value)
      input.value?.focus()
  })
}

const closeForm = () => {
  isFormVisible.value = false
}

const emits = defineEmits<{
  (event: 'add-todo', todo: ITodo): void
}>()

const todoText = ref<string>('')

const addTodo = () => {
  const newTodo: ITodo = {
    id: Date.now(),
    text: todoText.value,
    completed: false
  }

  emits('add-todo', newTodo)
  todoText.value = ''
}
</script>