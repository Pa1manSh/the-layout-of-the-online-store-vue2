<template>
  <div id="app">
    <AppHeader />

    <MainComponent />
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import MainComponent from "./components/MainComponent.vue";

export default {
  name: "App",
  components: { AppHeader, MainComponent },
};
</script>

<style>
body,
html {
  margin: 0;
  padding: 0;
}
</style>
