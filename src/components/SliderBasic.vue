<template>
<section>
  <h2>Slider Basic Example</h2>
  <p>In this example, we see how a reactive data property can be bound to a UI slider. 
    (See <a href="https://github.com/lab27/p8-vue/blob/main/src/components/SliderBasic.vue">/src/components/SliderBasic.vue</a>)</p>
  <!-- By using the directive "v-model" we bind the value of the slider to a reactive property called "value" -->
  <input type="range" v-model="value">
  <br>

  <!-- here is where we render the value of the property "value," which will update whenever the value changes -->
  <span>Slider value: {{value}}</span>

</section>
</template>

<script>
export default {
  name: 'SliderTest',
  // here we define the reactive data property "value"
  data() {
    return {
      value: 0
    }
  },
  methods: {
    // here we define the method "onChange" which is called when the slider value changes
    onChange(value) {
      this.value = value
    }
  }
}
</script>