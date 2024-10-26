<template>
  <form @submit.prevent="checkAvailability">
    <div>
      <label for="product-select">Select an product: </label>
      <select v-model="form.model" id="product-select" required>
        <option
          v-for="product in newProducts"
          :key="product.id"
          :value="product.item"
        >
          {{ product.item }}
        </option>
      </select>
    </div>
    <div>
      <label for="start-date">Start date: </label>
      <input type="date" v-model="form.dateRange.startDate" id="start-date" />
      <label for="end-date">End date: </label>
      <input type="date" v-model="form.dateRange.endDate" id="end-date" />
    </div>
    <button type="submit">Check availability</button>
    <p v-if="availabilityMessage">{{ availabilityMessage }}</p>
  </form>
</template>
<script setup lang="ts">
import { computed, ref } from 'vue'
interface Product {
  id: number
  item: string
}

const newProducts: Product[] = [
  {
    id: 1,
    item: 'Product 1',
  },
  {
    id: 2,
    item: 'Product 2',
  },
  {
    id: 3,
    item: 'Product 3',
  },
]

const form = {
  model: newProducts[0].item,
  dateRange: {
    startDate: '',
    endDate: '',
  },
}

const availabilityMessage = ref<string>('')

const isFormValid = computed<boolean>(() => {
  const start = new Date(form.dateRange.startDate)
  const end = new Date(form.dateRange.endDate)
  return start < end && form.model !== ''
})

const checkAvailability = () => {
  if (isFormValid.value) {
    const startDate = new Date(form.dateRange.startDate)
    const mockResponse =
      startDate.getDate() % 2 === 0
        ? null
        : new Date(startDate.setDate(startDate.getDate() + 1))
    if (mockResponse === null) {
      availabilityMessage.value = `${form.model} is available for the chosen period :).`
    } else {
      availabilityMessage.value = `${form.model} is unavailable for the chosen period, it is available from ${mockResponse.toLocaleDateString()}.`
    }
    return
  }
  availabilityMessage.value = 'Please select a valid date range.'
}
</script>
