<template>
  <div id="app">
    <days-list></days-list>
  </div>
</template>

<script>
import daysList from "./components/daysList";
export default {
  name: "App",
  components: {
    "days-list": daysList,
  },
};
</script>

<style>
body {
  margin: 0 !important;
}
#app {
  margin: 0;
  padding: 0;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #000;
  margin: 8px;
}
</style>
