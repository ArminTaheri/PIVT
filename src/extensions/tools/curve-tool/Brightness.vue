<template>
  <div class="container">
    <input class="slider" type="range" v-model="brightness"/>
    <input type="number" min="0" max="100" class="slider-value" v-model="brightness" />
  </div>
</template>

<script>
/**
 * curve-tool-widget renders the CanvasSpliner's DOM element
 * and allows the user to change the type of the spline.
 */
export default {
  name: 'brightness',
  props: ['controller'],
  mounted() {
    this.controller.setBrightness(this.brightness / 100);
  },
  data() {
    return { brightness: 0 };
  },
  watch: {
    brightness(v) {
      let vclamped = v;
      if (v > 100) { vclamped = 100; }
      if (v < 0) { vclamped = 0; }
      this.controller.setBrightness(vclamped / 100);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .slider {
    margin-top: 90px;
    width: 200px;
    -webkit-transform: rotate(-90deg);
        -ms-transform: rotate(-90deg);
            transform: rotate(-90deg);
  }
  .slider-value {
    margin-top: 117px;
    width: 40px;
  }
</style>
