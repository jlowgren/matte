<template>
  <div id="app">
    <Assignments />
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
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 0 auto;
  max-width: 50rem;
  color: #333;
  background: #efefef;
}
</style>
