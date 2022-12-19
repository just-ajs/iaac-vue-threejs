<template>

  <div id="sidebar" class="flex flex-col p-4">
    <div class="flex space-x-2 items-center">
      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-6 h-6">
        <path stroke-linecap="round" stroke-linejoin="round" d="M9.75 3.104v5.714a2.25 2.25 0 01-.659 1.591L5 14.5M9.75 3.104c-.251.023-.501.05-.75.082m.75-.082a24.301 24.301 0 014.5 0m0 0v5.714c0 .597.237 1.17.659 1.591L19.8 15.3M14.25 3.104c.251.023.501.05.75.082M19.8 15.3l-1.57.393A9.065 9.065 0 0112 15a9.065 9.065 0 00-6.23-.693L5 14.5m14.8.8l1.402 1.402c1.232 1.232.65 3.318-1.067 3.611A48.309 48.309 0 0112 21c-2.773 0-5.491-.235-8.135-.687-1.718-.293-2.3-2.379-1.067-3.61L5 14.5" />
      </svg>

      <h1 class="text-title text-xl font-bold font-sans">
        something with icon
      </h1>
    </div>

    <div class="p-5">
      <div class="w-full">
      <label for="slider">Slider that doesn't do anything</label>
      <input id="slider" type="range" class="w-full bg-gray-300 border-gray-300" v-model="sliderValue" min="0" max="100" step="10" />
      <p>slider: {{  sliderValue }}</p>
    </div>

  </div>


  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

 let sliderValue = ref(0)

</script>

<style>
</style>

<style scoped>
#sidebar {
  background: #e6edf2;
  margin: 12px;
  border-radius: 10px;
  left: 5;
  height: calc(100vh - 105px);
  width:450px;
  min-width: 200px;
}

</style>
