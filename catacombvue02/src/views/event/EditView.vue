<script setup lang="ts">
import type { Event } from '@/types'

defineProps<{
  event: Event
}>()
</script>

<template>
  <div v-if="event">
    <p>Edit event here[cite: 10]</p>
  </div>
</template>