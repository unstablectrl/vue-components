<template>
  <div id="app" class="container">
    <animation-inspect-3d :style="{ width: '600px', height: 'unset' }">
      <aspect-ratio-box :aspectRatio="5/3">
        <terminal :style="{ height: '100%' }"/>
      </aspect-ratio-box>
    </animation-inspect-3d>
  </div>
</template>

<script>
import Terminal from "./components/Terminal";
import AspectRatioBox from "./components/AspectRatioBox";
import AnimationInspect3d from "./components/AnimationInspect3d";

export default {
  name: "App",
  components: {
    AspectRatioBox,
    Terminal,
    AnimationInspect3d
  }
};
</script>

<style>
*,
*::after,
*::before {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: antiquewhite;
  background-color: #222;
  height: 100vh;
}
</style>
<style scoped>
.container {
  height: 100%;
  display: grid;
  place-items: center;
}
</style>
