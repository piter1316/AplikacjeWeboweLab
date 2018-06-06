<template>
  <div id="app">
  <main-component></main-component>
  </div>
</template>

<script>
import MainComponent from "./components/MainComponent.vue";
import "milligram";

export default {
  name: "app",
  components: {
    MainComponent
  }
};
</script>

