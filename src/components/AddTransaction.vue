<template>
  <!-- Section title -->
  <h3>Add new transaction</h3>

  <!-- Form submission handled by onSubmit() -->
  <!-- @submit.prevent stops page reload and calls function -->
  <form id="form" @submit.prevent="onSubmit()">

    <!-- Input field for transaction text -->
    <div class="form-control">
      <label for="text">Text</label>
      <!-- v-model binds input value to 'text' ref -->
      <input type="text" id="text" v-model="text" placeholder="Enter text..." />
    </div>

    <!-- Input field for amount -->
    <div class="form-control">
      <label for="amount">
        Amount <br />
        (negative - expense, positive - income)
      </label>
      <!-- v-model binds to 'amount' ref -->
      <input type="number" id="amount" v-model="amount" placeholder="Enter amount..." />
    </div>

    <!-- Submit button -->
    <button class="btn">Add transaction</button>
  </form>
</template>


<script setup>
// Import Vue Composition API helpers
import { ref } from 'vue';
// Import notification/toast library
import { useToast } from 'vue-toastification';

// Reactive state variables
const text = ref('');     // stores transaction description
const amount = ref('');   // stores transaction amount (as string initially)

// Define an event emitter (to send event to parent component)
const emit = defineEmits(['transactionSubmitted']);

// Initialize toast instance for showing error/success messages
const toast = useToast();

// Function runs when form is submitted
const onSubmit = () => {
  // Validation: check if both fields are filled
  if (!text.value || !amount.value) {
    toast.error('Both fields must be filled'); // show error
    return;
  }

  // Create transaction object
  const transactionData = {
    text: text.value,                  // description
    amount: parseFloat(amount.value)   // amount as a number
  };

  // Emit custom event to parent with new transaction
  emit('transactionSubmitted', transactionData);

  // Clear input fields
  text.value = '';
  amount.value = '';
};
</script>
