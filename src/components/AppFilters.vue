<template>
  <aside class="app-filters">
    <section class="toggle-group">
      <button
        v-for="filter in filters"
        :key="filter"
        class="button"
        :class="{ 'button--primary': activeFilter === filter }"
        @click="setFilter(filter)"
      >{{ filter }}</button>
      <!-- <button
        class="button"
        :class="{ 'button--primary': activeFilter === 'Active' }"
      >Active</button>
      <button
        class="button"
        :class="{ 'button--primary': activeFilter === 'Done' }"
      >Done</button> -->
    </section>
  </aside>
</template>

<script setup lang="ts">
import { PropType, ref } from 'vue';
import { Filter } from '../types/Filters';

const props = defineProps({
  activeFilter: {
    type: String as PropType<Filter>,
    required: true
  }
})

const filters = ref<Filter[]>(['All', 'Active', 'Done'])

const emits = defineEmits({
  'set-filter': (filter: Filter) => true
})
const setFilter = (filter: Filter) => {
  emits('set-filter', filter)
}
</script>