<template>
    <div>
        <ul>
            <li v-for="movie in store.movies">
                {{ movie.title }}
                {{ movie.original_title }}
                <!-- {{ film.original_language }} -->
                <span class="fi" :class="'fi-'+movie.original_language"></span>
                {{ movie.vote_count }}
            </li> 
        </ul>
    </div>
</template>

<script>
    import { store } from '../store.js'
    export default {
        
    }
</script>

<style lang="scss" scoped>

</style>