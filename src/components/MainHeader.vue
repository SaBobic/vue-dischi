<template>
    <header>
        <nav class="d-flex align-items-center">
            <img src="../assets/img/spotify-logo-png-7053.png" alt="Spotify Logo">
        </nav>
    </header>
</template>

<script>
export default {
    name: 'MainHeader',
}
</script>

<style lang="scss" scoped>
@import '../assets/scss/vars';

nav {
    padding: 0 20px;
    height: 70px;
    background-color: $secondary_color;

    img {
        height: 50px;
    }
}
</style>