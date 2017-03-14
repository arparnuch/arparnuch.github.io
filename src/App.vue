<template>
  <div id="app">

    <!-- <img src="./assets/logo.png"> -->
    <iccs340-left-sidenav></iccs340-left-sidenav>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app',
  components: {
    Iccs340LeftSidenav: require('./LeftSidenav')
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /*margin-top: 60px;*/
}

html{
  background-image: url('./assets/water2.jpg');
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
  color: black;
  height: 100%;
  align-items: center;
}
</style>
