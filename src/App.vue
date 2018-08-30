<template>
  <div id="app">
    <h1>reggio</h1>
    <hr />

    <Cards/>
    <hr />
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
  font-family: "Lucida Console";
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
hr {
  border: 0;
  height: 0;
  border-top: 1px solid rgba(0, 0, 0, 0.1);
  border-bottom: 1px solid rgba(255, 255, 255, 0.3);
}
</style>
