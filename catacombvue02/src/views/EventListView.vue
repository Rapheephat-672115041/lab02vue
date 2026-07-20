<script setup lang="ts">
import EventCard from '@/components/EventCard.vue';
import type { Event } from '@/types'
import { ref, onMounted } from 'vue'
import EventDetails from '@/components/EventDetails.vue'
import axios from 'axios'

const events = ref<Event[] | null>(null)

onMounted(() => {
  axios
    .get('https://my-json-server.typicode.com/Rapheephat-672115041/testserverlab02componentthingy/events')
    .then(response => {
      console.log(response.data)
    })
    .catch(error => {
      console.error('There was an error!', error);
    });
});
</script>

<template>
  <h1>Events For Good</h1>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event"/>
    <EventDetails v-for="event in events" :key="event.category + event.organizer" :event="event"/>
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
