
<template>
  <div class="container">
    <el-button v-if="show" class="axes-checkbox" @click="toggleAxes" type="primary">
      Hide Axes
    </el-button>
    <el-button v-else class="axes-checkbox" @click="toggleAxes">
      Show Axes
    </el-button>
  </div>
</template>

<script>
/**
 * ortho-view-camera-axes-widget offers sidebar buttons for the user to show and
 * hide the axes in the viewports.
 */
export default {
  name: 'ortho-view-camera-axes-widget',
  props: ['controller'],
  data() {
    return { show: true };
  },
  methods: {
    toggleAxes() {
      this.show = !this.show;
      this.controller.showAxes(this.show);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
