<template>
  <base-app-bar-top></base-app-bar-top>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <main-page></main-page>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

import { MainPage } from './pages';
import { BaseAppBarTop } from '@/shared';

export default defineComponent({
  name: 'App',
  components: {
    MainPage,
    BaseAppBarTop,
  },
});
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body {
  margin: 0;
}
</style>
