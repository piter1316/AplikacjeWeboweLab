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
<style>
#app{
  margin-top: 25px;
  margin-left: auto;
  margin-right: auto;
  width: 1000px;
  background: beige;
  border-radius: 20px;
}
</style>

