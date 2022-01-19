<template>
<section>
  <h2>Slider Rotation Example</h2>
  <p>In this example, let's use the slider value to set a rotation property on an element. (See src/components/SliderRotation.vue)</p>
  <p>We only have to set the <code>transform-origin</code> property of the image to the x/y values of the pivot point. Then we can simply bind the <code>transform: rotate([x]deg)</code> style declaration to the slider value, where <code>x</code> = the slider value.</p>
  
  <p>The blue arrow is a separate html element that we can also rotate inversely.</p>
  <input type="range" min="20" max="90" value="90" class="slider" id="myRange2" step="1" v-model="rotation"> 
  <br>
  <span>Plate angle ϕ: {{rotation}}°</span>
  <br>
  <br>
  <input type="range" min="0" max="100" value="50" class="slider" id="myRange3" step="1" v-model="arrowLength"> 
  <br>
  <span>Arrow length: {{arrowLength}}</span>
  <div class="graphic" :style="`transform: scale(.75) rotate(${rotation-90}deg)`">

  <img src="/img/panel.png" alt="Panel To Rotate" class="panel" >
  <div class="arrow-wrapper" :style="`transform: rotate(${(rotation * -1)+90}deg)`" v-show="arrowLength > 0">
    <div class="arrow-stem" :style="`width: ${arrowLength}%`"></div>
    <div class="arrow-head"></div>
  </div>
  </div>
</section>
</template>

<script>
export default {
  name: 'SliderTest',
  data() {
    return {
      rotation: 90,
      arrowLength: 50,
    }
  },
  methods: {
    onChange(value) {
      this.value = value
    }
  }
}
</script>

<style>
.graphic {
  position: relative;
  display: block;
  width: 800px;
  transform-origin: 268px 264px;
  /* border: 1px dotted #000; */
  margin: 0 auto;
  pointer-events: none;
}
img.panel {
  width: 800px;
  height: 750px;
  transform-origin: 268px 264px;
  pointer-events: none;
}

.arrow-wrapper {
  position: absolute;
  display: flex;
  justify-items: flex-end;
  align-items: center;
  transform-origin: right bottom;
  left: -91px;
  top: 400px;
  width: 200px;
  height: 10px;
  z-index: 1;
  filter: drop-shadow(0 1px 2px rgba(0,0,0,.5));
}

.arrow-head {
  position: absolute;
  right: -10px;
  width: 1px;
  height: 1px;
  border: 10px solid transparent;
  border-left-color: dodgerblue;
}

.arrow-stem {
  position: absolute;
  right: 10px;
  height: 5px;
  width: 50px;
  background: dodgerblue;
  margin-left: auto;
}
</style>