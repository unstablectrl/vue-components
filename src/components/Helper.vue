<template>
  <div id="helper">
    <span>{{text}}</span>
  </div>
</template>

<script>
export default {
  props: {
    text: String
  }
};
</script>


<style scoped>
#helper {
  color: black;
  background: white;
  border: 1px solid white;
  position: fixed;
  right: 0;
  top: 0;
}
</style>
