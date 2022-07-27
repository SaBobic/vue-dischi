<template id="app">
  <div>
    <MainHeader @select="getGenreValue" :genres="albumsGenres" />
    <MainContent :albums="filteredAlbums" :is-loading="isLoading" />
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
      albums: [],
      isLoading: false,
      selectedGenre: '',
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
    },
    filteredAlbums() {
      return this.albums.filter(album => {
        return album.genre.toLowerCase().includes(this.selectedGenre);
      }
      )
    },
  },
  methods: {
    getAlbumsArray() {
      this.isLoading = true;
      axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then(res => {
          this.isLoading = false;
          return this.albums = res.data.response;
        })
    },
    getGenreValue(value) {
      return this.selectedGenre = value;
    },
  },
  created() {
    this.getAlbumsArray();
  }
}
</script>

<style lang="scss">
@import './assets/scss/style.scss';
</style>