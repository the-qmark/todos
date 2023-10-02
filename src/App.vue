<template>
  <AppHeader />

  <AppFilters />

  <main class="app-main">
    <AppTodoList />

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

const onAddTodo = (todo: ITodo) => {
  console.log(todo);
}
</script>