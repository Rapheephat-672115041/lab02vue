<script setup lang="ts">
import type { Event } from '@/types'

defineProps<{
  event: Event
}>()
</script>

<template>
  <div v-if="event">
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}[cite: 8]</p>
    <p>{{ event.description }}[cite: 8]</p>
  </div>
</template>