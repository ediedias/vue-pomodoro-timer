<script setup>
import { defineProps, computed } from 'vue';

const props = defineProps({'time': Number});

const formattedTime = computed(() => {
  const minutes = Math.floor(props.time / 60);
  const seconds = props.time % 60;
  return `${String(minutes).padStart(2, '0')}:${String(seconds).padStart(2, '0')}`;
});

</script>

<template>
<div class="text-4xl font-bold text-center">
     <div>
     {{ formattedTime }} 
     </div>
</div>
</template>