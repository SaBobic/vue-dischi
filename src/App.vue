<template id="app">
  <div>
    <MainHeader @genre="getGenreValue" @author="getAuthorValue" :genres="albumsGenres" :authors="albumsAuthors"
      :selected-author="selectedAuthor" />
    <MainContent :albums="filteredAlbumsByAuthor" :is-loading="isLoading" />
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
      selectedAuthor: '',
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
    albumsAuthors() {
      const newArray = [];
      const authors = [];
      this.filteredAlbumsByGenre.forEach(album => {
        if (!authors.includes(album.author)) {
          authors.push(album.author);
        }
      });
      authors.forEach(author => {
        const obj = {
          value: author.toLowerCase(),
          text: author,
        };
        newArray.push(obj);
      });
      return newArray;
    },
    filteredAlbumsByGenre() {
      return this.albums.filter(album => album.genre.toLowerCase().includes(this.selectedGenre));
    },
    filteredAlbumsByAuthor() {
      return this.filteredAlbumsByGenre.filter(album => album.author.toLowerCase().includes(this.selectedAuthor));
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
      this.selectedAuthor = '';
      return this.selectedGenre = value;
    },
    getAuthorValue(value) {
      return this.selectedAuthor = value;
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