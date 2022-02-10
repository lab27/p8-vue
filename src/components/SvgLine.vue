<template>
  <section>
    <h2>SVG Line Example</h2>
    <p>
      In this example, we see how we can animate different SVG line properties
      with Vue.js. (See /src/components/SvgLine.vue)
    </p>
    <p>Here we use a simple CSS Keyframe animation to animate the <code>stroke-dashoffset</code> property of an SVG line, and then bind the <code>stroke-dasharray</code> property to calculations from the slider value.</p>
    <p>If we want, we can also map the throttle percentage to a Hue value and bind it to the stroke color of the line.</p>
    <input type="range" v-model="valve" min="278" max="4444" step="1" />
    <br>
    <span><strong>mbar:</strong> {{ valve }}</span>
    <br>
    <span><strong>Throttle open:</strong> {{ throttleOpenPercent }}%</span>
    <br>
    <span><strong>Water Hue:</strong> <span :style="`color: hsl(${waterHue},50%,50%)`">{{ waterHue }}</span></span>
    <br>
    <br>
    <svg width="800" height="200" class="stream" :style="`animation-duration:${animationDuration}ms`">
      <line
        x1="10"
        y1="10"
        x2="800"
        y2="10"
        :stroke="`hsl(${waterHue}, 50%, 50%)`"
        stroke-width="10"
        :style="`stroke-dasharray: ${(100-throttleOpenPercent) + 10} ${throttleOpenPercent+20};`"
      />
    </svg>
  </section>
</template>

<script>
export default {
  data() {
    return {
      valve: 910,
    };
  },
  computed: {
    throttleOpenPercent() {
      const throttleOpenPercent = (this.valve - 278) / (4444 - 278);
      return Math.floor(throttleOpenPercent * 100);
    },
    animationDuration() {
      return 6000 - this.valve;
    },
    waterHue() {
      return Math.floor(this.map(this.throttleOpenPercent, 0, 100, 180, 360))
    },
  },
  methods: {
    // map a number from 1 range to another
    map(n, start1, end1, start2, end2) {
      return ((n - start1) / (end1 - start1)) * (end2 - start2) + start2;
    },
  },
};
</script>

<style scoped>
.stream {
  animation: flow linear forwards infinite;
  stroke-linecap:round;
}

@keyframes flow {
  0% {
    stroke-dashoffset: 0;
  }
  100% {
    stroke-dashoffset: -800;
  }
}
  
</style>