<template>
  <Header />
  <Fact />
</template>

<script>
import Header from "./components/Header.vue";
import Fact from "./components/Fact.vue";

export default {
  name: "App",
  components: {
    Header,
    Fact,
  },
};
</script>

<style>
#app {
  font-family: "Open Sans", sans-serif;
  text-align: center;
  color: #2c3e50;
}
</style>
