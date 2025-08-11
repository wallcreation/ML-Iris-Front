<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import Form from './components/Form.vue'
import Output from './components/Output.vue'
import { ref } from 'vue'
import axios from 'axios'
const formData = ref(null)
const resultData = ref(null)
const isLoading = ref(false)

async function handleFormSubmit(data) {
  formData.value = data
  try {
    isLoading.value = true
    const response = await axios.post('http://localhost:8000/iris/predict', data)
    resultData.value = response.data
  } catch (error) {
    console.error('Error during form submission:', error)
  } finally {
    isLoading.value = false
  }
}
</script>

<template>
  <Header />
  <main class="w-full flex-grow flex flex-col md:flex-row gap-2 rounded-lg p-4">
    <Form :isLoading="isLoading" @submit="handleFormSubmit" />
    <Output :isLoading="isLoading" :data="formData" :result="resultData" />
  </main>
  <Footer />
</template>

<style scoped></style>
