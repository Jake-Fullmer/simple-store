<template>
  <div id="app">
    <navbar-component />
    <div>
      <router-view />
    </div>
  </div>
</template>

<script>
import NavbarComponent from "./components/NavbarComponent";

export default {
  name: "App",
  data() {
    return {};
  },
  components: {
    NavbarComponent
  }
};
</script>

<style lang="scss">
@import "bootstrap";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
