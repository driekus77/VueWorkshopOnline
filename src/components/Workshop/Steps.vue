<template>
  <div class="wrapper">
    <center>
      <div class="header">
        <div class="inner">
          <div class="StepSelector">
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
        </div>
      </div>
    </center>

    <div class="content">
      <div class="inner">
        <div class="scrollable">
          <Step class="CurrentStep" :value="currentStep"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Step from "./Step";

export default {
  name: "Steps",
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
.CurrentStep {
  position: relative;
  text-align: left;
}

.CurrentStep > * {
  font-family: "Roboto";
}

.StepSelector > label {
  font-weight: bolder;
  font-size: 18pt;
  margin-right: 25px;
  width: 100%;
  text-align: center;
}

.StepSelector > select {
  color: var(--bloemertdark-color);
  font-weight: bolder;
  font-size: 18pt;
  border-style: none;
  border-width: none;
}
</style>
