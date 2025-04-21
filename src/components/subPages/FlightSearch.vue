<script setup>
import { ref } from "vue";

const tripType = ref("round");
</script>

<template>
  <div class="flight-container">
    <v-radio-group v-model="tripType" class="trip-toggle" hide-details inline>
      <v-radio
        label="Round Trip"
        value="round"
        class="radio-option pb-3 active-border"
      />
      <v-radio label="One Way" value="oneway" class="radio-option pb-3" />
    </v-radio-group>

    
  </div>
</template>

<style lang="scss" scoped>
.flight-container {
  height: 600px;
  max-width: 520px;
  margin: 0 auto;
}
.radio-option {
  width: 50%;
  font-size: 20px;
  border-bottom: 2px solid;
}
.active-border {
  border-color: red;
}
::v-deep(.v-selection-control__wrapper) {
  display: none;
}
::v-deep(.trip-toggle .v-label) {
  font-size: 20px !important;
  font-weight: 300;
}
</style>
