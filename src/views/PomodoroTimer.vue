<script setup>
import { ref } from 'vue';

const WORK_TIME = 25 * 60; //25 * 60 seconds
const BREAK_TIME = 5 * 60; //25 * 60 seconds

const time = ref(WORK_TIME);
</script>

<template>
     <div class="text-center">
          <div>
              {{ time }} 
          </div>
     </div>
</template>