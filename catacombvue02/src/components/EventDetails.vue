<script setup lang="ts">
import type { Event } from '@/types'

defineProps<{
  event: Event
}>()
</script>

<template>
  <div class="event-details">
    <div>{{ event.category }}</div>
    <div>{{ event.organizer }}</div>
  </div>
</template>

<style scoped>
.event-details {
  text-align: right;
}
</style>