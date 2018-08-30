<template>
  <div id="app">
    <h1>regio</h1>
    <Cards/>
    <Cash />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld';
import Cards from './components/Cards';
import Cash from './components/Cash';

export default {
  name: 'App',
  components: {
    Cards,
    Cash,
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
h1 {
  color: #232e3a;
}
img {
  max-height: 1em;
}
</style>
