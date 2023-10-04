<template>
  <AppHeader />

  <AppFilters
    :active-filter="activeFilter"
    @set-filter="onSetFilter"
  />

  <main class="app-main">
    <AppTodoList
      :todos="filteredTodos"
      @toggle-todo="onToggleTodo"
      @delete-todo="onDeleteTodo"
    />

    <AppAddTodo @add-todo="onAddTodo" />
  </main>

  <AppFooter
    :number-active="activeTodos.length"
    :number-done="doneTodos.length"
  />

  <ThemeButton />
</template>

<script setup lang="ts">
import AppHeader from './components/AppHeader.vue'
import AppFilters from './components/AppFilters.vue'
import AppTodoList from './components/AppTodoList.vue'
import AppAddTodo from './components/AppAddTodo.vue'
import AppFooter from './components/AppFooter.vue'
import { ITodo } from './types/Todo'
import { computed, ref } from 'vue'
import { Filter } from './types/Filters'
import ThemeButton from './components/ThemeButton.vue'

const activeFilter = ref<Filter>('All')

const onSetFilter = (filter: Filter) => {
  activeFilter.value = filter
}

const todos = ref<ITodo[]>([])

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

const filteredTodos = computed((): ITodo[] => {
  switch (activeFilter.value) {
    case 'Active':
      return activeTodos.value
    case 'Done':
      return doneTodos.value
    case 'All':
    default:
      return todos.value
  }
})

const activeTodos = computed((): ITodo[] => {
  return todos.value.filter((todo: ITodo) => !todo.completed)
})

const doneTodos = computed((): ITodo[] => {
  return todos.value.filter((todo: ITodo) => todo.completed)
})
</script>