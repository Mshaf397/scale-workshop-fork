<script setup lang="ts">
import { formatHertz, formatExponential, formatCents } from '@/utils'

const props = defineProps<{
  label: string
  cents: number
  ratio: number
  frequency: number
  showLabel: boolean
  showCents: boolean
  showRatio: boolean
  showFrequency: boolean
}>()
</script>

<template>
  <div class="key-info">
    <div v-if="props.showLabel">
      <strong>{{ props.label }}</strong>
    </div>
    <div v-if="props.showCents">{{ formatCents(props.cents, 0) }}</div>
    <div v-if="props.showRatio">{{ formatExponential(props.ratio) }}</div>
    <div v-if="props.showFrequency">{{ formatHertz(props.frequency) }}</div>
  </div>
</template>

<style scoped>
.keyboard-grid {
  display: grid;
  /* 14 equal columns, 20 equal rows */
  grid-template-columns: repeat(14, 1fr);
  grid-template-rows: repeat(20, 1fr);
  
  /* Occupy the full viewport */
  width: 100vw;
  height: 100vh;
  gap: 2px; /* Optional gap between keys */
  box-sizing: border-box;
}

.key {
  width: 100%;
  height: 100%;
  min-width: 0;  /* Prevents grid blowout from inner text */
  min-height: 0; /* Prevents grid blowout from inner text */
  
  display: flex;
  align-items: center;
  justify-content: center;
}

.key-info {
  font-size: clamp(0.6rem, 1.5vh, 1.25em); /* Scales font size dynamically */
  text-shadow: 1px 1px 1px rgba(255, 255, 255, 0.3);
}


[data-theme='dark'] .key-info {
  text-shadow: 1px 1px 1px rgba(0, 0, 0, 0.3);
}

.dark .key-info {
  color: white;
  text-shadow: none;
}

.light .key-info {
  color: black;
  text-shadow: none;
}
</style>
