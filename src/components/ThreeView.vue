<template>
  <div class="three-mount">
    <canvas class="three-mount-canvas"></canvas>
  </div>
</template>

<script>
import * as THREE from 'three';
/**
 * When the three-view component is mounted, a threejs WebGLRenderer
 * is instantiated and the renderer and canvas is passed to its associated layout.
 */
export default {
  name: 'three-view',
  props: ['controller', 'name'],
  mounted() {
    const canvas = this.$el.querySelector('.three-mount-canvas');
    const renderer = new THREE.WebGLRenderer({ canvas, antialias: false });
    renderer.setViewport(0, 0, canvas.width, canvas.height);
    renderer.setScissor(0, 0, canvas.width, canvas.height);
    renderer.setClearColor(new THREE.Color().setRGB(1.0, 1.0, 1.0));
    renderer.clear(true, true, true);
    this.controller.resolveCanvas3d(this.name, renderer, canvas);
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
canvas.three-mount-canvas {
  width: 100% !important;
  height: 100% !important;
  background-color: #fff;
}
</style>
