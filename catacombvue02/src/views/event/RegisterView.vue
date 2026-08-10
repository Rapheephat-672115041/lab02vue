<script setup lang="ts">
import type { Event } from '@/types'
import { toRefs } from 'vue'
import { useRouter } from 'vue-router'

 const props =defineProps <{
  event: Event
}>()

const { event } = toRefs(props)
const router = useRouter() 

const register = () => {
  router.push({ name: 'event-detail-view', params: { id: event.value.id } })
}
</script>

<template>
  <div v-if="event">
    <p>Register event here</p>

    <button @click="register">Register</button>
  </div>
</template>