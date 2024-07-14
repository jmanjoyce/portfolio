<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/> -->
  <!-- <h1> hi</h1> -->
  <PortfolioPage></PortfolioPage>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
//import HelloWorld from './components/HelloWorld.vue';
import PortfolioPage from './components/PortfolioPage.vue';

export default defineComponent({
  name: 'App',
  components: {
    PortfolioPage
  }
});
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
