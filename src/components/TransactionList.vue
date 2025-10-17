<template>
  <h3>History</h3>
  <ul id="list" class="list">

    <!-- Loop through transactions -->
    <li 
      v-for="transaction in transactions" 
      :key="transaction.id"
      :class="transaction.amount < 0 ? 'minus' : 'plus'"
    >
      <!-- Show text + amount -->
      {{ transaction.text }}
      <span>${{ transaction.amount }}</span>

      <!-- Delete button -->
      <button 
        @click="deleteTransaction(transaction.id)" 
        class="delete-btn"
      >
        x
      </button>
    </li>
  </ul>
</template>


<script setup>
import { defineProps } from 'vue'

// Event emitter
const emit = defineEmits(['transactionDeleted'])

// Props from parent
const props = defineProps({
  transactions: {
    type: Array,
    required: true,
  },
})

// Emit event with transaction id
const deleteTransaction = (id) => {
  emit('transactionDeleted', id)
}
</script>
