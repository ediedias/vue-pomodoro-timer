<script setup>
import { defineProps } from 'vue';

defineProps({
     isRunning: {
          type: Boolean,
          required: true
     }
});

</script>

<template>     
    <div class="flex justify-between">
      <button @click="$emit('start')" 
        class="text-white px-4 py-2 rounded"
        :class="{'bg-blue-500': !isRunning, 'bg-blue-200': isRunning }" :disabled="isRunning">Start</button>
      <button @click="$emit('pause')" class="bg-yellow-500 text-white px-4 py-2 rounded">Pause</button>
      <button @click="$emit('reset')" class="bg-red-500 text-white px-4 py-2 rounded">Reset</button>
    </div>
</template>