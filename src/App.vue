<template>
  <AppHeader />

  <AppFilters />

  <main class="app-main">
    <AppTodoList
      :todos="todos"
      @toggle-todo="onToggleTodo"
      @delete-todo="onDeleteTodo"
    />

    <AppAddTodo @add-todo="onAddTodo" />
  </main>

  <AppFooter />
</template>

<script setup lang="ts">
import AppHeader from './components/AppHeader.vue'
import AppFilters from './components/AppFilters.vue'
import AppTodoList from './components/AppTodoList.vue'
import AppAddTodo from './components/AppAddTodo.vue'
import AppFooter from './components/AppFooter.vue'
import { ITodo } from './types/Todo'
import { ref } from 'vue'

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

const onAddTodo = (todo: ITodo) => {
  todos.value.push(todo)
}
</script>