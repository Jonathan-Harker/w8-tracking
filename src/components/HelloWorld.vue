<template>
  <div class="weight-tracker">
    <h2>Weight Tracker</h2>

    <div class="input-group">
      <label>Starting Weight:</label>
      <div class="weight-input">
        <div class="input-wrapper">
          <input
            type="number"
            v-model="startingWeightStones"
            placeholder="Stones"
          />
        </div>
        <div class="input-wrapper">
          <input
            type="number"
            v-model="startingWeightPounds"
            placeholder="Pounds"
          />
        </div>

        <label>Current Weight:</label>
        <div class="weight-input">
          <div class="input-wrapper">
            <input
              type="number"
              v-model="currentWeightStones"
              placeholder="Stones"
            />
          </div>
          <div class="input-wrapper">
            <input
              type="number"
              v-model="currentWeightPounds"
              placeholder="Pounds"
            />
          </div>
        </div>

        <label>Target Weight:</label>
        <div class="weight-input">
          <div class="input-wrapper">
            <input
              type="number"
              v-model="targetWeightStones"
              placeholder="Stones"
            />
          </div>
          <div class="input-wrapper">
            <input
              type="number"
              v-model="targetWeightPounds"
              placeholder="Pounds"
            />
          </div>
        </div>
      </div>
    </div>

    <div class="progress-bar">
      <div class="progress" :style="{ width: progressPercentage + '%' }"></div>
    </div>

    <p>Progress: {{ progressPercentage }}%</p>
  </div>
</template>

<script>
export default {
  name: "WeightTracker",
  data() {
    return {
      startingWeightStones: 0,
      startingWeightPounds: 0,
      currentWeightStones: 0,
      currentWeightPounds: 0,
      targetWeightStones: 0,
      targetWeightPounds: 0,
    };
  },
  computed: {
    progressPercentage() {
      // Convert weights to a common unit (e.g., pounds)
      const startingWeight =
        this.startingWeightStones * 14 + this.startingWeightPounds;
      const currentWeight =
        this.currentWeightStones * 14 + this.currentWeightPounds;
      const targetWeight =
        this.targetWeightStones * 14 + this.targetWeightPounds;

      if (targetWeight === 0) {
        return 0;
      }

      return (
        ((currentWeight - startingWeight) / (targetWeight - startingWeight)) *
        100
      );
    },
  },
};
</script>

<style scoped>
.weight-input {
  display: flex;
  flex-direction: column;
  gap: 10px; /* Adjust the gap as needed */
}
</style>