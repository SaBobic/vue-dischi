<template>
    <header class="d-flex justify-content-between align-items-center">
        <nav class="d-flex align-items-center">
            <img src="../assets/img/spotify-logo-png-7053.png" alt="Spotify Logo" type="button">
        </nav>
        <div>
            <StandardSelect @select="sendAuthor" placeholder="Filtrare per autore" :options="authors" />
            <StandardSelect @select="sendGenre" placeholder="Filtrare per genere" :options="genres" />
        </div>
    </header>
</template>

<script>
import StandardSelect from './StandardSelect.vue';

export default {
    name: "MainHeader",
    props: {
        genres: Array,
        authors: Array,
    },
    components: { StandardSelect },
    methods: {
        sendAuthor(value) {
            return this.$emit('author', value);
        },
        sendGenre(value) {
            return this.$emit('genre', value);
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/scss/vars';

header {
    padding: 0 20px;
    height: 70px;
    background-color: $secondary_color;

    img {
        height: 50px;
    }
}
</style>