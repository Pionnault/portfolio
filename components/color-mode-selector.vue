<template>
  <div class="flex space-x-2 items-center">
    <div v-if="showNextModeLabel" class="text-gray-500 text-xs">Change to {{ nextMode }}</div>
    <button
      @click="toggleMode"
      class="hover:bg-gray-200 dark:hover:bg-gray-600 px-2 py-1 text-gray-500"
      @mouseenter="showNextModeLabel = true"
      @mouseleave="showNextModeLabel = false"
    >
      {{ nextModeIcon }}
    </button>
  </div>
</template>

<script setup>
const colorMode = useColorMode()

const showNextModeLabel = ref(false)

const modes = ['system', 'light', 'dark']

const nextModeIcons = {
  system: '🌓',
  light: '🌕',
  dark: '🌑'
}

const nextMode = computed(() => {
  const nextMode = modes.indexOf(colorMode.preference)
  return nextMode + 1 === modes.length ? modes[0] : modes[nextMode + 1]
})

const nextModeIcon = computed(() => nextModeIcons[nextMode.value])

function toggleMode() {
  colorMode.preference = nextMode.value
}
</script>

<style></style>
