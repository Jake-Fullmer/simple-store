<template>
  <div class="home">
    <navbar-component />
    <main-component />
  </div>
</template>

<script>
// @ is an alias to /src
import MainComponent from "@/components/MainComponent.vue";
import NavbarComponent from "@/components/NavbarComponent";

export default {
  name: "Home",
  components: {
    NavbarComponent,
    MainComponent
  }
};
</script>
