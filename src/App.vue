<script setup>
import PomodoroTimer from './views/PomodoroTimer.vue';
import { ref, computed } from 'vue';

const WORK_TIME = 25 * 60; //25 * 60 seconds
const BREAK_TIME = 5 * 60; //25 * 60 seconds

const time = ref(WORK_TIME);
const intervalId = ref(null);

const startTimer = () => {
   intervalId.value = setInterval(() => {
    if(time.value > 0) {
      time.value--;
    } else {
      clearInterval(intervalId);
    }
  }, 1000);
};

const formattedTime = computed(() => {
  const minutes = Math.floor(time.value / 60);
  const seconds = time.value % 60;
  return `${String(minutes).padStart(2, '0')}:${String(seconds).padStart(2, '0')}`;
});

</script>

<template>
  <div class="container flex flex-col gap-5">
    <h1 class="text-2xl font-bold text-center">Pomodoro Timer</h1>
    
    <div class="text-4xl font-bold text-center">
      <div>
          {{ formattedTime }} 
      </div>
    </div>
    
    <div class="flex justify-between">
      <button @click="startTimer" class="bg-blue-500 text-white px-4 py-2 rounded">Start</button>
      <button class="bg-yellow-500 text-white px-4 py-2 rounded">Pause</button>
      <button class="bg-red-500 text-white px-4 py-2 rounded">Reset</button>
    </div>
  </div>
</template>