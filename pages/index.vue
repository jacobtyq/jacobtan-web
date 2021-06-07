<template>
  <div id="app">
    <app-header />
      <app-body />
    <app-footer />
  </div>
</template>

<script>
import Header from '@/sections/Header'
import Footer from '@/sections/Footer'

import Body from '@/sections/Body'

export default {
  name: 'App',
  components: {
    'app-header': Header,
    'app-footer': Footer,
    'app-body': Body
  }
}

if(process.client) {
  var WebFont = require('webfontloader')

  WebFont.load({
    google: {
      families: ['Fira Sans', 'Roboto']
    }
  })
}
</script>

<style lang='scss'>
#app {
  $max-width: 960px;

  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #1A535C;
  margin-top: 60px;
  // width: $max-width;
  max-width: 100%;

  margin: 0 auto;

  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 0;
  text-rendering: optimizeLegibility;
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
}

html,body {
  height: 100%;
}

header{
  font-family: 'GFS Didot', serif;
}
</style>