<template>
  <div class="content">
    <div id="StepSelector">
      <label for="step">Choose a step:</label>
      <select id="step" v-model="currentStep">
        <option value="Step-0_Welcome_Goal.md">0. Welcome & Goals</option>
        <option value="Step-1_Basics.md">1. Basics</option>
        <option value="Step-2_Conditionals_Loops.md">2. Conditionals & Loops</option>
        <option value="Step-3_Events_Data.md">3. Events & Data</option>
        <option value="Step-4_Data_Binding.md">4. Data Binding</option>
        <option value="Step-5_State_Management.md">5. State Management</option>
        <option value="Step-6_Next_Level.md">6. Next Level</option>
      </select>
    </div>
    <Step :value="currentStep"/>
  </div>
</template>

<script>
import Step from "./Step";

export default {
  name: "App",
  data() {
    return {
      currentStep: "Step-0_Welcome_Goal.md"
    };
  },
  components: {
    Step
  }
};
</script>

<style>
.content {
  flex: 1 0 auto;
  /* Prevent Chrome, Opera, and Safari from letting these items shrink to smaller than their content's default minimum size. */
  padding: 10px;

  text-align: left;
}
</style>
