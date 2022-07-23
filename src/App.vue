<template>

  <div id="app">
    <Home></Home>
  </div>

</template>

<script>

import Home from './components/Home'

export default {
  name: 'App',
  components: {
    Home
  }
}

</script>

<style>

body {
  font-family: 'Darker Grotesque', sans-serif;
  background: #fff url(https://i.imgur.com/74w2YOr.jpg) center center no-repeat;
  background-size: cover;
}

</style>
