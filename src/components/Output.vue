<script setup>
import { computed } from 'vue'
const props = defineProps({
  data: {
    type: Object,
  },
})

const data = computed(()=> props.data)

</script>
<template>
  <div class="w-1/2 p-4 bg-gray-900 rounded-lg">
    <h2 class="text-xl text-center">Prediction result</h2>
    <div>
      <p class="font-bold text-fuchsia-500">
        Sepal Length In Input:
        <span>{{ props.data?.sepalLength || 'N/A' }}</span>
      </p>
      <p class="font-bold text-fuchsia-500">
        Sepal Width In Input:
        <span>{{ props.data?.sepalWidth || 'N/A' }}</span>
      </p>
      <p class="font-bold text-fuchsia-500">
        Petal Length In Input:
        <span>{{ props.data?.petalLength || 'N/A' }}</span>
      </p>
      <p class="font-bold text-fuchsia-500">
        Petal Width In Input:
        <span>{{ props.data?.petalWidth || 'N/A' }}</span>
      </p>
      <p class="mt-5 font-bold">Predicted Name: {{ data?.prediction }}</p>
      <p class="mt-5 font-bold">Predicted Confidence: {{ data?.confidence }}</p>
    </div>
  </div>
</template>
