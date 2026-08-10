<script setup lang="ts">
import type { Event } from '@/types'

defineProps<{
  event: Event
}>()
</script>

<template>
  <div v-if="event">
    <p>Register event here[cite: 9]</p>
  </div>
</template>