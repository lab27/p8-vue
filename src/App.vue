<template>
  <div id="app">
    <h1>P8 Test Project using Vue.js</h1>
    <p>Prepared by <a href="mailto:nick@nickniles.com">Nick Niles</a></p>
    <slider-basic></slider-basic>
    <slider-rotation></slider-rotation>
    <svg-line></svg-line>
    <machine></machine>
  </div>
</template>

<script>
import SliderBasic from './components/SliderBasic.vue'
import SliderRotation from './components/SliderRotation.vue'
import SvgLine from './components/SvgLine.vue'
import Machine from './components/Machine.vue'
// load the library and ALL languages
const hljs = require('highlight.js');

export default {
  name: 'App',
  components: {
    SliderBasic,
    SliderRotation,
    SvgLine,
    Machine
  },
  mounted() {
    // highlight code blocks
    document.querySelectorAll('pre code').forEach((block) => {
      hljs.highlightBlock(block);
    });
  }
}
</script>

<style>
html {
  font-size: 18px;
}
body {
  overflow-x: hidden;
  padding: clamp(1rem, 4vw, 2rem);
  background-color: #f9f9f9;
}

h1 {
  font-size: clamp(3rem, 5vw, 5rem);
  margin: 0;
}

#app {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}

section {
  margin-bottom: 2rem;
  padding: 2rem;
  background-color: #fff;
  box-shadow: 0 4px 20px rgba(0,0,0,.1);
}

section p {
  /* max-width: 720px; */
  margin: 0 auto;
  line-height: 1.5;
  text-align: left;
  margin-bottom: 1rem;
}
</style>
