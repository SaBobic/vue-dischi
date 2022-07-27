<template>
    <header class="d-flex justify-content-between align-items-center">
        <nav class="d-flex align-items-center">
            <img src="../assets/img/spotify-logo-png-7053.png" alt="Spotify Logo" type="button">
        </nav>
        <div>
            <StandardSelect placeholder="Filtrare per genere" :options="albumsGenres" />
        </div>
    </header>
</template>

<script>
import StandardSelect from './StandardSelect.vue';

export default {
    name: "MainHeader",
    props: {
        albums: Array,
    },
    components: { StandardSelect },
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