<template>
  <!-- Heading -->
  <h4>Your Balance</h4>

  <!-- Display the balance passed in as a prop -->
  <!-- `total` comes from parent component -->
  <h1 id="balance">${{ total }}</h1>
</template>


<script setup>
// Import defineProps to declare props in <script setup>
import { defineProps } from 'vue';

// Define the props this component accepts
// 'total' is a Number and required
const props = defineProps({
  total: {
    type: Number,
    required: true,
  },
});
</script>
