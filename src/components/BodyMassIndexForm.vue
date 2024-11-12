<script setup>
import { ref } from 'vue'

// inputted height and weight is stored here
const userHeight = ref()
const userWeight = ref()

// this is used to be able to send arguments to App.vue
const emit = defineEmits(['stats-entered'])

// function to run when user clicks the button
// this function will emit a message to App.vue including
// the user's height and weight data
function sendBmi() {
  emit('stats-entered', userHeight.value, userWeight.value)
}
</script>

<template>
  <div id="bmif">
<!--    v-models for input height and weight, data is stored in their respective variables -->
    <h2>Enter your height and weight</h2>
    <label>Height in meters: </label><input v-model="userHeight">
    <br>
    <label>Weight in kilograms: </label><input v-model="userWeight">
    <br>
  <!--  v-on to tell the script when the user clicks the button -->
    <button v-on:click="sendBmi">Calculate</button>
  </div>
</template>

<style scoped>
#bmif {
  border: red 5px solid;
  padding: 20px
}

button {
  border: black 1px solid;
  margin: 10px;
}
</style>
