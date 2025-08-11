<script setup>
import { computed, ref } from 'vue'

const props = defineProps(['isLoading'])
const emits = defineEmits(['submit'])

const sepalLength = ref('')
const sepalWidth = ref('')
const petalLength = ref('')
const petalWidth = ref('')
const isLoading = computed(() => props.isLoading)
const err = ref('')

function onSubmit() {
  if (!sepalLength.value || !sepalWidth.value || !petalLength.value || !petalWidth.value) {
    err.value = 'All fields are required.'
    setInterval(() => {
      err.value = ''
    }, 10000)
    return
  }
  const data = {
    sepal_length: sepalLength.value,
    sepal_width: sepalWidth.value,
    petal_length: petalLength.value,
    petal_width: petalWidth.value,
  }
  emits('submit', data)
}
</script>
<template>
  <div class="md:w-1/2 space-y-1.5">
    <h2 class="py-2 bg-gray-900 rounded-lg text-center text-2xl">Enter the flower measurements</h2>
    <div v-if="err" class="px-6" :class="err ? 'animate-bounce' : ''">
      <p class="p-2 rounded-lg bg-red-500">{{ err }}</p>
    </div>
    <form action="" method="post" class="px-2 grid grid-cols-2 md:flex md:flex-col gap-2">
      <input
        type="number"
        step="0.01"
        name="sepal_length"
        id="sepal_length"
        placeholder="Sepal Length"
        v-model="sepalLength"
        class="p-2 rounded-lg bg-white text-fuchsia-950 font-bold outline-none border-2 border-white focus:bg-gray-900 focus:text-fuchsia-500 focus:border-fuchsia-500"
      />
      <input
        type="number"
        step="0.01"
        name="sepal_width"
        id="sepal_width"
        placeholder="Sepal Width"
        v-model="sepalWidth"
        class="p-2 rounded-lg bg-white text-fuchsia-950 font-bold outline-none border-2 border-white focus:bg-gray-900 focus:text-fuchsia-500 focus:border-fuchsia-500"
      />
      <input
        type="number"
        step="0.01"
        name="petal_length"
        id="petal_length"
        placeholder="Petal Length"
        v-model="petalLength"
        class="p-2 rounded-lg bg-white text-fuchsia-950 font-bold outline-none border-2 border-white focus:bg-gray-900 focus:text-fuchsia-500 focus:border-fuchsia-500"
      />
      <input
        type="number"
        step="0.01"
        name="petal_width"
        id="petal_width"
        placeholder="Petal Width"
        v-model="petalWidth"
        class="p-2 rounded-lg bg-white text-fuchsia-950 font-bold outline-none border-2 border-white focus:bg-gray-900 focus:text-fuchsia-500 focus:border-fuchsia-500"
      />
      <div class="col-span-2 flex justify-center">
        <button
          @click.prevent="onSubmit"
          :disabled="isLoading"
          :class="isLoading ? 'animate-pulse' : ''"
          class="px-4 py-2 rounded-lg bg-violet-600 hover:bg-fuchsia-500 disabled:bg-gray-900"
        >
          {{ isLoading ? 'Loading...' : 'Submit' }}
        </button>
      </div>
    </form>
  </div>
</template>
