<template>
  <div id="app">
    <!-- <OrgInfoTile /> -->
    <AboutMe />
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
// import OrgInfoTile from "./components/OrgInfoTile.vue";
import AboutMe from "./components/AboutMe.vue";

export default {
  name: "App",
  components: {
    // HelloWorld,
    // OrgInfoTile,
    AboutMe,
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
