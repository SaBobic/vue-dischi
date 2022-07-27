<template id="app">
  <div>
    <MainHeader />
    <MainContent :albums="albums" :is-loading="isLoading" />
  </div>
</template>

<script>
import MainHeader from './components/MainHeader.vue';
import MainContent from './components/MainContent.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    MainHeader,
    MainContent,
  },
  data() {
    return {
      albums: null,
      isLoading: false,
    }
  },
  computed: {
    albumsGenres() {
      const newArray = [];
      const genres = [];
      this.albums.forEach(album => {
        if (!genres.includes(album.genre)) {
          genres.push(album.genre);
        }
      });
      genres.forEach(genre => {
        const obj = {
          value: genre.toLowerCase(),
          text: genre,
        };
        newArray.push(obj);
      });
      return newArray;
    }
  },
  methods: {
    getAlbumsArray() {
      this.isLoading = true;
      axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then(res => {
          this.isLoading = false;
          return this.albums = res.data.response;
        })
    }
  },
  created() {
    this.getAlbumsArray();
  }
}
</script>

<style lang="scss">
@import './assets/scss/style.scss';
</style>