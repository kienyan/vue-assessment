<script setup lang="ts">
import WebDesign from './components/WebDesign.vue'
import FormPicker from './components/FormPicker.vue'
import { ref } from 'vue'

const currentAssignment = ref('FormPicker')
const toggleAssignment = () => {
  if (currentAssignment.value === 'FormPicker') {
    currentAssignment.value = 'WebDesign'
  } else {
    currentAssignment.value = 'FormPicker'
  }
}
</script>

<template>
  <main>
    <nav class="navigation">
      <button class="toggleAssignment" @click="toggleAssignment()">
        {{ currentAssignment }}
      </button>
    </nav>
    <FormPicker v-if="currentAssignment === 'FormPicker'" />
    <WebDesign v-else />
  </main>
</template>
<style>
.navigation {
  display: flex;
  justify-content: center;
}
.toggleAssignment {
  padding: 1rem;
}
</style>
