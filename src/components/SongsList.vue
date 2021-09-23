<template>
  <section class="songs-container d-flex justify-content-center align-items-center">
    <div v-if="!loading" class="container row">
      <!-- Stampo la lista delle canzoni ottenuta tramite Axios API -->
      <Song v-for="(song, index) in filteredAlbums" 
        :key="index"
        :info="song" class="single-song"/>
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
  props: ['lastValue'],
  components: {
    Song,
    Loader
  },
  data() {
    return {
      APIUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
      songsList: [],
      loading: true,
      genreArray: []
    }
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
    },
    getGenre() {
            axios
                .get(this.APIUrl)
                .then( response => {
                    let array = response.data.response;
                    for (let i = 0; i < array.length; i++) {
                        if (!this.genreArray.includes(array[i].genre)) {
                            this.genreArray.push(array[i].genre)
                        } 
                    }
                })
                this.$emit('genreArr', this.genreArray);
        }
    },
  computed: {
        filteredAlbums() {
            if (this.lastValue == '') {
                return this.songsList
            } else {
                const filteredArray = this.songsList.filter((element) => {
                    if(element.genre == this.lastValue) {
                        return element;
                    } 
                });
                return filteredArray;
            }
        },
  },
  created() {
    this.getSongs();
    this.getGenre();
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