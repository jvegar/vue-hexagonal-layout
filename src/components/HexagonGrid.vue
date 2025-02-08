<template>
  <div class="main">
    <div class="container">
      <Hexagon
        v-for="hex in hexagons"
        :key="hex.name"
        :label="hex.name"
        :color="hex.color"
        :style="calculatePosition(hex.position)"
      />
    </div>
  </div>
</template>

<script>
import Hexagon from "./Hexagon.vue";

export default {
  components: {
    Hexagon,
  },
  data() {
    return {
      hexagons: [
        { name: "JS", position: { x: 0, y: 0 }, color: "#cb1116" },
        { name: "TS", position: { x: 0.63, y: 0 }, color: "#02aae9" },
        { name: "C#", position: { x: 0, y: 0.63 }, color: "#a6dc00" },
        { name: "Java", position: { x: -0.63, y: 0.63 }, color: "#e9a61b" },
        { name: "Html", position: { x: -0.63, y: 0 }, color: "#d905e7" },
        { name: "X", position: { x: 0, y: -0.63 }, color: "#d905e7" },
      ],
    };
  },
  methods: {
    calculatePosition(position) {
      // Size of hexagon + margin (from CSS variables)
      const size = 45;
      const margin = 5;

      // Calculate the offset for centering (you might need to adjust these values)
      const xOffset = size * 1.5;
      const yOffset = size * 1.732;

      // Calculate actual position
      // For hexagonal grid, we need to offset every other row
      const x = position.x * xOffset;
      const y = position.y * yOffset + (position.x % 2) * (yOffset / 2);

      return {
        left: `calc(50% + ${x}px)`,
        top: `calc(50% + ${y}px)`,
      };
    },
  },
};
</script>

<style scoped>
.main {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  --s: 45px; /* size  */
  --m: 5px; /* margin */
  --f: calc(1.732 * var(--s) + 4 * var(--m) - 1px);
}

.container {
  font-size: 0; /*disable white space between inline block element */
  position: relative;
  width: 100%;
  height: 100%;
}

.container div {
  width: var(--s);
  margin: var(--m);
  height: calc(var(--s) * 1.1547);
  display: inline-block;
  font-size: initial;
  clip-path: polygon(0% 25%, 0% 75%, 50% 100%, 100% 75%, 100% 25%, 50% 0%);
  background: #262626;
  position: absolute;
  transform: rotate(30deg);
  font-size: large;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>
