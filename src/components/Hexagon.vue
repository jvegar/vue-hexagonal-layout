<template>
  <div class="hexagon" :style="{ color: color }">
    <span class="text">{{ label }}</span>
  </div>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      required: true,
    },
    color: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
.text {
  transform: rotate(-30deg);
}
</style>
