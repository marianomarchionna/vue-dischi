<template>
  <header>
    <div class="img-logo ms-3">
      <img src="../assets/spotify.png" alt="Logo Spotify">
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../styles/general';
header {
    height: 70px;
    width: 100%;
    background: #2e3a46;
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
