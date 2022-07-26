<template id="app">
  <div>
    <MainHeader />
    <MainContent :albums="albums" />
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
    }
  },
  methods: {
    getAlbumsArray() {
      axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then(res => { return this.albums = res.data.response; })
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