<!-- src/App.vue -->
<template>
  <div id="app">
    <HexagonGrid />
    <!-- Include the HexagonGrid component -->
  </div>
</template>

<script>
import HexagonGrid from "./components/HexagonGrid.vue"; // Import the HexagonGrid component

export default {
  components: {
    HexagonGrid, // Register the HexagonGrid component
  },
};
</script>

<style>
html {
  background: radial-gradient(
    circle,
    rgba(140, 142, 141, 1) 0%,
    rgba(75, 77, 76, 1) 100%
  );
}
</style>
