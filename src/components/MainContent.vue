<template>
    <main class="d-flex align-items-center">
        <div class="container">
            <StandardLoader v-if="isLoading" />
            <div v-else class="row g-3">
                <div v-for="album in albums" class="col-auto" :key="album.title">
                    <AlbumSingle :poster="album.poster" :title="album.title" :author="album.author"
                        :year="album.year" />
                </div>
            </div>
        </div>
    </main>
</template>

<script>
import AlbumSingle from "./AlbumSingle.vue";
import StandardLoader from "./StandardLoader.vue";

export default {
    name: "MainContent",
    components: { AlbumSingle, StandardLoader, },
    props: {
        albums: Array,
        isLoading: Boolean,
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/scss/vars';

main {
    background-color: $primary_color;
    height: calc(100vh - 70px);

    .col-auto {
        flex-basis: calc(100% / 5);

        .album {
            background-color: $secondary_color;

            .band,
            .year {
                color: $grey;
            }

            .band {
                font-size: 20px;
            }
        }
    }

}
</style>