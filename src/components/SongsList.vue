<template>
  <section class="songs-container d-flex justify-content-center align-items-center">
    <div v-if="!loading" class="container row">
      <!-- Stampo la lista delle canzoni ottenuta tramite Axios API -->
      <div v-for="(song, index) in songsList" :key="index" class="single-song">
        <Song :info="song" />
      </div>
    </div>
    <Loader v-else />
  </section>
</template>

<script>
import axios from 'axios';
import Song from "./Song.vue";
import Loader from './Loader.vue';
export default {
  name: 'SongsList',
  components: {
    Song,
    Loader
  },
  data() {
    return {
      APIUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
      songsList: [],
      loading: true
    }
  },
  created() {
    this.getSongs();
  },
  methods: {
    getSongs() {
      axios
          .get(this.APIUrl)
          .then( res => {
            this.songsList = res.data.response;
            this.loading = false;
          })
          .catch( err => {
            console.log("Error ", err);
          })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../styles/general';
.songs-container{
    width: 100%;
    min-height: calc(100vh - 70px);
    background: $bg-main;
    .single-song{
        flex-basis: calc(100% / 5 - 10px);
        margin: 5px;
        cursor: pointer;
    }
}

</style>