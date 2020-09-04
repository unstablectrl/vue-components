<template>
  <div :class="['aspect-ratio-box', {center}]" :style="cssVars">
    <div class="aspect-ratio-box-inside">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    aspectRatio: {
      type: Number,
      default: 16 / 9,
    },
    // Note: center doesn't work if parent component has no height
    center: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    cssVars() {
      return {
        '--aspect-ratio': this.aspectRatio,
      }
    },
  },
}
</script>

<style scoped>
.aspect-ratio-box {
  /* --aspect-ratio: calc(5/3); */
  position: relative;
  padding-bottom: calc(100%/var(--aspect-ratio));
  height: 0;
}

.aspect-ratio-box.center {
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%)
}

.aspect-ratio-box-inside {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
/* debug */
/* .aspect-ratio-box {
  background-color: rgba(138, 43, 226 , .2);
  border: 1px solid blueviolet;
} */
</style>
