<script setup lang="ts">
import type { Event } from '@/types'
import { toRefs } from 'vue'
import { useRouter } from 'vue-router'
import { useMessageStore } from '@/stores/message'

 const props =defineProps <{
  event: Event
}>()

const { event } = toRefs(props)
const router = useRouter()
const store = useMessageStore()

const register = () => {
  store.updateMessage(`You are successfully registered for the ${props.event.title}!`)
  setTimeout(() => {
    store.resetMessage()
  }, 3000)
  router.push({ name: 'event-detail-view', params: { id: props.event.id } })
}
</script>

<template>
  <div v-if="event">
    <p>Register event here</p>

    <button @click="register">Register me!</button>
  </div>
</template>