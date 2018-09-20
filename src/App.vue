<template>
  <div id="app">

    <MainPage />
  </div>
</template>

<script>
import MainPage from './components/Main'


export default {
  name: 'App',
  components: {
    MainPage
  }

}
</script>

<style>
  body, html { width: 100%; height: 100%; min-height: 100%; margin: 0; }
  #app { width: 100%; height: 100%; }
</style>
