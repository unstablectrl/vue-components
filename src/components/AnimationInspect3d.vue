<template>
  <div id="animationInspect3d">
    <div
      class="wrapper"
      @mousemove="onMouseMove"
      @mouseleave="onMouseLeave"
      ref="animationInspect3d"
      :style="cssVars"
    >
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    delayDefault: 500,
    transitionDelay: 500,
    transitionType: "ease-out",
    off: true,
    rotationDefault: { x: 0, y: -0 },
    rotation_: { x: -0, y: 0 },
    rotationMultiplier: -10
  }),
  methods: {
    onMouseMove(e) {
      if (this.off) {
        setTimeout(() => {
          if (!this.off) {
            this.transitionDelay = 50;
            this.transitionType = "ease";
          }
        }, this.delayDefault);
      }

      const pos = { x: e.clientX, y: e.clientY };
      const newRotation = this.calculateRotation(pos, this.boundaries);
      this.rotation = newRotation;

      this.off = false;
    },
    calculateRotation(pos, boundaries) {
      const { width, height, left, top } = boundaries;
      const relX = pos.x - left;
      const relY = pos.y - top;
      const rotX = (relY / height) * -2 + 1;
      const rotY = (relX / width) * 2 - 1;
      return { x: rotX, y: rotY };
    },
    onMouseLeave(e) {
      this.off = true;
      this.transitionDelay = this.delayDefault;
      this.transitionType = "ease-out";
      setTimeout(
        () => (this.rotation = this.rotationDefault),
        this.delayDefault / 4
      );
    }
  },
  computed: {
    boundaries() {
      return this.$refs["animationInspect3d"].getBoundingClientRect();
    },
    rotation: {
      get: function() {
        return this.rotation_;
      },
      set: function(rot) {
        Object.assign(this.rotation_, {
          x: rot.x * this.rotationMultiplier,
          y: rot.y * this.rotationMultiplier
        });
      }
    },
    cssVars() {
      return {
        "--rotate-x": this.rotation.x,
        "--rotate-y": this.rotation.y,
        "--transition-delay": this.transitionDelay,
        "--transition-type": this.transitionType
      };
    }
  }
};
</script>

<style scoped>
#animationInspect3d {
  perspective: 1000px;
}
#animationInspect3d > .wrapper {
  height: inherit;
  transition: transform calc(1ms * var(--transition-delay)) var(--transition-type);
  transform: translate3d(0,0,-00px) rotateX(calc(1deg * var(--rotate-x))) rotateY(calc(1deg * var(--rotate-y)));
}
/* debug */
/* #animationInspect3d {
  background-color: rgba(0, 255, 0, 0.2);
  border: 2px solid green;
}
#animationInspect3d > .wrapper {
  background-color: rgba(255, 0, 0, 0.2);
  border: 2px solid red;
} */
</style>

