<template>
  <div id="app">
    <InfoTile />
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import InfoTile from "./components/InfoTile.vue";

export default {
  name: "App",
  components: {
    // HelloWorld,
    InfoTile,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  background-color: #212a40;
}
</style>
