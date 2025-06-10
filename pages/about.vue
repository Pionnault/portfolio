<template>
  <div>This page is about me.</div>
  <button @click="onClick">Click Me!</button>
</template>

<script setup lang="ts">
definePageMeta({
  layout: 'custom'
})

function onClick(): void {
  setPageLayout('default')
}
</script>
