<template>
    <div class="album p-3 text-center">
        <img src="https://i.discogs.com/psDUUalbwHXuzNS7QgK93aG6ImE4JzALnOkCPtB1HVw/rs:fit/g:sm/q:40/h:300/w:300/czM6Ly9kaXNjb2dz/LWRhdGFiYXNlLWlt/YWdlcy9SLTEyNDY5/NTMtMTQ0ODkyNzA4/Ni02NTkwLmpwZWc.jpeg"
            alt="" class="img-fluid mb-3">
        <h4>NEW JERSEY</h4>
        <div class="band">Bon Jovi</div>
        <div class="year">1988</div>
    </div>
</template>

<script>
export default {
    name: 'AlbumSingle',
}
</script>

<style lang="scss" scoped>
@import '../assets/scss/vars';

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
</style>