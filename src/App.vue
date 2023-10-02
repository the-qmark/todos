<template>
  <AppHeader />

  <AppFilters />

  <main class="app-main">
    <AppTodoList />

    <AppAddTodo />
  </main>

  <AppFooter />
</template>

<script setup lang="ts">
import AppHeader from './components/AppHeader.vue'
import AppFilters from './components/AppFilters.vue'
import AppTodoList from './components/AppTodoList.vue'
import AppAddTodo from './components/AppTodoList.vue'
import AppFooter from './components/AppFooter.vue'

</script>

<style></style>
