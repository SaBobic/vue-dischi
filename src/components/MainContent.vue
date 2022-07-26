<template>
    <main class="d-flex align-items-center">
        <div class="container">
            <div class="row g-3">
                <div class="col-auto">
                    <AlbumSingle />
                </div>
            </div>
        </div>
    </main>
</template>

<script>
import AlbumSingle from "./AlbumSingle.vue";

export default {
    name: "MainContent",
    components: { AlbumSingle }
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