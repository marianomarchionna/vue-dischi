<template>
  <div id="app" class="text-center">
    <Header/> 
    <SongsList/> 
  </div>
</template>

<script>
import Header from './components/Header.vue'
import SongsList from './components/SongsList.vue'

export default {
  name: 'App',
  components: {
    Header,
    SongsList
  }
}
</script>

<style lang="scss">
@import './styles/general';
#app {
  width: 100%;
  height: 100vh;
}
</style>