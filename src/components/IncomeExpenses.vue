<template>
  <!-- Wrapper for income and expense display -->
  <div class="inc-exp-container">
    
    <!-- Income block -->
    <div>
      <h4>Income</h4>
      <!-- 'income' comes from props -->
      <p id="money-plus" class="money plus">+${{ income }}</p>
    </div>

    <!-- Expense block -->
    <div>
      <h4>Expense</h4>
      <!-- 'expenses' comes from props -->
      <p id="money-minus" class="money minus">${{ expenses }}</p>
    </div>

  </div>
</template> 


<script setup>
// Import Vue helper to define props
import { defineProps } from 'vue'

// Define expected props (must be numbers)
const props = defineProps({
  income: {
    type: Number,
    required: true,
  },
  expenses: {
    type: Number,
    required: true,
  },
})
</script>
