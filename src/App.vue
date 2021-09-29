<template>
  <div id="app">
    <father></father>
  </div>
</template>

<script>
import Father from "./components/father/index.vue";

export default {
  name: "App",
  components: {
    Father,
  },
};
</script>

<style  scoped lang='less'>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

  width: 100%;
  height: 500px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
