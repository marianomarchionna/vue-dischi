<template>
  <div id="app" class="text-center">
    <Header
    @emitGenre="getGenre" 
    :allGenre="genreArray"
    />
    <main>
    <SongsList 
    @genreArr="getArrGenre"
    :lastValue="selectValue" />
    </main>
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
  },
  data() {
    return {
      selectValue: '',
      genreArray: []
    }
  },
  methods: {
    getGenre(value) {
      this.selectValue = value;
    },
    getArrGenre(array) {
      this.genreArray = array;
    }
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