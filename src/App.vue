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
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;400&display=swap");

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
::-webkit-scrollbar {
  width: 10px;
}
::-webkit-scrollbar-thumb {
  background: crimson;
  border-radius: 10px;
}
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 15px gold;
  border-radius: 10px;
}
::-webkit-scrollbar {
  width: 10px;
}
::-webkit-scrollbar-thumb {
  background: crimson;
  border-radius: 10px;
}
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 15px gold;
  border-radius: 10px;
}
html {
  height: 100%;
  width: 100%;
  font-family: "Roboto", sans-serif;
}
body {
  height: 100%;
  width: 100%;
  margin: 0px;
  padding: 0px;
  scroll-behavior: none;
  display: flex;
  justify-content: center;
}
</style>
