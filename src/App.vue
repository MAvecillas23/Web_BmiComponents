<script setup>
import BodyMassIndexForm from "./components/BodyMassIndexForm.vue";
import { ref } from 'vue'

// after calculations bmi will be stored here
const bmi = ref(0)

// function that calculates emitted height and weight from BodyMassIndexForm.vue
// to get bmi and assign that value to the bmi variable
function calculateBmi(height, weight){
  bmi.value = weight / (height * height)

}

</script>

<template>
  <div id="app-component">
    <h1>Body Mass Index Calculator</h1>
<!--    get emitted data from BodyMassIndexForm using v-on and then calling the calculateBmi function-->
    <BodyMassIndexForm v-on:stats-entered="calculateBmi"></BodyMassIndexForm>

<!--bmi rounded to two decimal places-->
    <p> Your BMI is {{ bmi.toFixed(2) }}</p>
  </div>
</template>

<style scoped>
#app-component {
  border: blue 5px solid;
  padding: 40px
}

</style>
