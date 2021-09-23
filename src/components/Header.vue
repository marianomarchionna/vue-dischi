<template>
  <header>
    <div class="img-logo ms-3 me-3 d-flex justify-content-between">
      <img src="../assets/spotify.png" alt="Logo Spotify">
      <form> 
        <label for="genre"></label>
        <select v-model="inputValue" 
          @change="$emit('emitGenre', inputValue)" 
          name="genre" id="genre">
          <option value="">All</option>
          <option v-for="(genre, index) in allGenre" :key="index" :value="genre">{{ genre }}</option>
        </select>
      </form>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
    props: ['allGenre'],
    data() {
        return {
            inputValue: ''
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../styles/general';
header {
    height: 70px;
    width: 100%;
    background: $bg-header;
    .img-logo{
      height: 100%;
      display: flex;
      align-items: center;
  
      img{
        height: 70%;
      }
    }
  }
</style>