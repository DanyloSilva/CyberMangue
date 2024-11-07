<template>
  <div id="app" style="background-color: black; color: white;">
    <div class="container">
      <GoogleMap />
    </div>
  </div>
</template>

<script>
import GoogleMap from "./components/GoogleMap.vue";

export default {
  name: "App",
  components: {
    GoogleMap,
  },
};
</script>

<style>
.container {
  padding: 20px;
}
</style>
