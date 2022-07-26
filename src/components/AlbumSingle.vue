<template>
    <div class="album p-3 text-center">
        <img :src="poster" :alt="title" class="img-fluid mb-3">
        <h4>{{ title }}</h4>
        <div class="author">{{ author }}</div>
        <div class="year">{{ year }}</div>
    </div>
</template>

<script>
export default {
    name: 'AlbumSingle',
    props: {
        poster: String,
        title: String,
        author: String,
        year: String,
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/scss/vars';

.album {
    height: 100%;
    background-color: $secondary_color;

    .author,
    .year {
        color: $grey;
    }

    .author {
        font-size: 20px;
    }
}
</style>