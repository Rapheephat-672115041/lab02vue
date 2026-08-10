<script setup lang="ts">
import { ref, onMounted } from 'vue'
import EventService from '@/services/EventService'
import type { Event } from '@/types'

const props = defineProps({
  id: {
    type: String,
    required: true
  }
})

const event = ref<Event | null>(null)

onMounted(() => {
  EventService.getEvent(Number(props.id))
    .then((response) => {
      event.value = response.data
    })
    .catch((error) => {
      console.error('There was an error!', error)
    })
})
</script>

<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <nav>
      <!-- เอา params: { id } ออก เพราะ Router จะจัดการให้อัตโนมัติใน Nested Route -->
      <RouterLink :to="{ name: 'event-detail-view' }">Details</RouterLink> |
      <RouterLink :to="{ name: 'event-register-view' }">Register</RouterLink> |
      <RouterLink :to="{ name: 'event-edit-view' }">Edit</RouterLink>
    </nav>

    <RouterView :event="event" />
  </div>
</template>

<style scoped>
nav {
  padding-bottom: 20px;
}
nav a {
  font-weight: bold;
  color: #2c3e50;
  margin: 0 5px;
}
nav a.router-link-exact-active {
  color: #42b983;
}
</style>