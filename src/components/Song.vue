<template>
  <div class="song mb-2 d-flex flex-column justify-content-around align-items-center text-center p-1">
    <div class="image">
            <img :src="info.poster" class="img-fluid" :alt="info.title">
        </div>
        <h3 class="title">
            {{info.title}}
        </h3>
        <div>
            <span class="author d-block">
                {{info.author}}
            </span>
            <span class="year d-block">
                {{info.year}}
            </span>
        </div>
  </div>
</template>
<script>
export default {
  name: 'Song',
  props: ['info']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../styles/general';

.song{
    background: $bg-header;
    min-height: 250px;
    flex-basis: 200px;
    flex-wrap: wrap;
    .image{
        width: 150px;
        img{
            width: 100%;
        }
    }
    .title{
        text-transform: uppercase;
        color: $white;
        font-size: 15px;
        font-weight: bold;
    }
    .author, .year{
        color: $gray;
        font-size: 12px;
    }
}
</style>