<script setup>
import TimerControls from '../components/TimerControls.vue';
import TimerDisplay from '../components/TimerDisplay.vue';

import { ref, onUnmounted } from 'vue';

const WORK_TIME = 25 * 60; //25 * 60 seconds
const BREAK_TIME = 5 * 60; //25 * 60 seconds

const time = ref(WORK_TIME);
const currentTimer = ref('work');
const isRunning = ref(false);
const intervalId = ref(null);

const startTimer = () => {
  if (!isRunning.value) {
    isRunning.value = true;
    intervalId.value = setInterval(() => {
      if(time.value > 0) {
        time.value--;
      } else {
        isRunning.value = false;
        clearInterval(intervalId.value);
        if (currentTimer.value === 'work') {
          currentTimer.value = 'break';
          time.value = BREAK_TIME;
        } else {
          currentTimer.value = 'work';
          time.value = WORK_TIME;
        }
        startTimer();
      }
    }, 1000);
  }
};

const pauseTimer = () => {
  isRunning.value = false;
  clearInterval(intervalId.value);
};

const resetTimer = () => {
  isRunning.value = false;
  clearInterval(intervalId.value);
  time.value = WORK_TIME;
};

onUnmounted(() => {
  clearInterval(intervalId.value);
});
</script>

<template>
     <TimerDisplay :time="time" />
     <TimerControls 
          :isRunning="isRunning"
          @start="startTimer"
          @pause="pauseTimer"
          @reset="resetTimer"
          />
</template>