<script setup>
import { computed } from 'vue'
const props = defineProps({
  data: {
    type: Object,
  },
  result: {
    type: Object,
  },
})

const data = computed(() => props.data)
const result = computed(() => props.result)
</script>
<template>
  <div class="md:w-1/2 p-4 bg-gray-900 rounded-lg">
    <h2 class="text-xl text-center">Prediction result</h2>
    <div>
      <p class="font-bold text-fuchsia-500">
        Sepal Length In Input:
        <span>{{ data?.sepal_length || 'N/A' }}</span>
      </p>
      <p class="font-bold text-fuchsia-500">
        Sepal Width In Input:
        <span>{{ data?.sepal_width || 'N/A' }}</span>
      </p>
      <p class="font-bold text-fuchsia-500">
        Petal Length In Input:
        <span>{{ data?.petal_length || 'N/A' }}</span>
      </p>
      <p class="font-bold text-fuchsia-500">
        Petal Width In Input:
        <span>{{ data?.petal_width || 'N/A' }}</span>
      </p>
      <p class="mt-5 font-bold">Predicted Name: {{ result?.prediction }}</p>
      <p class="mt-5 font-bold">Predicted Confidence: {{ result?.confidence }}</p>
    </div>
  </div>
</template>
