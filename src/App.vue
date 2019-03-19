<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script>
import Assignments from './components/Assignments';

export default {
  name: 'App',
  components: {
    Assignments,
  },
};
</script>

<style>
*,
*::before,
*::after {
  box-sizing: inherit;
}

html {
  font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 0 auto;
  max-width: 50rem;
  color: #fff;
  text-shadow: 1px 1px rgba(0, 0, 0, 0.5);
  background: #3b653d;
}
</style>
