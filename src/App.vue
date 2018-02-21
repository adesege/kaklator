<template>
  <div id="app">
    <Calculator />
  </div>
</template>

<script>
import Calculator from './components/Calculator';

export default {
  name: 'App',
  components: {
    Calculator,
  },
};
</script>

<style lang='scss'>
  :root {
    font-size: 16px;
  }

  body {
    background-color: #fafafa;
    max-height: 100vh;
    height: 100%;
  }
</style>
