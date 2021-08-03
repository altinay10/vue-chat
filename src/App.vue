<template>
  <container />
</template>

<script>
import Container from "./components/container.vue";

export default {
  name: "App",
  components: {
    Container,
  },
};
</script>

<style>
#app {
  font-family: Whitney, "Helvetica Neue", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
html {
  height: 100%;
  width: 100%;
}
</style>
