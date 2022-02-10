<template>
<section>
  <h2>Slider Basic Example</h2>
  <p>In this example, we see how a reactive data property can be bound to a UI slider. 
    (See /src/components/SliderBasic.vue)</p>
  <input type="range" v-model="value">
  <br>


  <span>Slider value: {{value}}</span>

</section>
</template>

<script>
export default {
  name: 'SliderTest',
  data() {
    return {
      value: 0
    }
  },
  methods: {
    onChange(value) {
      this.value = value
    }
  }
}
</script>