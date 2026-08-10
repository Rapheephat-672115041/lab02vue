<script setup lang="ts">
import { ref, onMounted } from 'vue'
import StudentService from '@/services/StudentService'
import type { Student } from '@/student'
import { useRouter } from 'vue-router'

const students = ref<Student[] | null>(null)
const router = useRouter()

onMounted(() => {
  StudentService.getStudents()
    .then((response) => {
      students.value = response.data
    })
    .catch((error) => {
      console.error('Error fetching students:', error)
      router.push({ name: 'network-error-view' })
    })
})
</script>

<template>
  <div class="student-list">
    <h1>Student List</h1>
    <div v-for="student in students" :key="student.id" class="student-card">
      <h2>{{ student.name }} {{ student.surname }}</h2>
      <p>GPA: {{ student.gpa }}</p>
    </div>
  </div>
</template>

<style scoped>
.student-card {
  border: 1px solid #ccc;
  padding: 1rem;
  margin: 1rem;
  border-radius: 8px;
}
</style>