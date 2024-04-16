<template>
    <div>
        <h2>FILMS</h2>
        <ul>
            <li v-for="film in store.films">
                {{ film.name }}
                {{ film.original_name }}
                <!-- {{ film.original_language }} -->
                <span class="fi" :class="'fi-'+film.original_language"></span>
                {{ film.vote_count }}
                <img :src="`https://image.tmdb.org/t/p/${this.store.widthImg}${film.poster_path}`" alt="">
            </li>
        </ul>
    </div>
</template>

<script>
    import { store } from '../store.js'
    export default {
        data() {
            return {
                store,
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>