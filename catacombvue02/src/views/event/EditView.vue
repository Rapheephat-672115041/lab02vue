<script setup lang="ts">
import type { Event } from '@/types'
import { toRefs } from 'vue'
import { useRouter } from 'vue-router'
import { useMessageStore } from '@/stores/message'

const props = defineProps<{
  event: Event
}>()

const { event } = toRefs(props)
const router = useRouter()
const store = useMessageStore()

const handleUpdate = () => {
  store.updateMessage('Data has been updated')
  setTimeout(() => {
    store.resetMessage()
  }, 5000)
  router.push({ name: 'event-detail-view', params: { id: props.event.id } })
}
</script>

<template>
  <div v-if="event">
    <p>Edit event here</p>
    <button @click="handleUpdate">Update event details</button>
  </div>
</template>