<template>
  <footer class="app-footer">{{ numberActive }} more to do, {{ numberDone }} done</footer>
</template>

<script setup lang="ts" >
import { defineProps } from 'vue'

const props = defineProps({
  numberActive: {
    type: Number,
    default: 0
  },
  numberDone: {
    type: Number,
    default: 0
  },
})

</script>