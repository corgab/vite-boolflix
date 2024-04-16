<template>
    <div>
        <h2>MOVIES</h2>
        <ul>
            <li v-for="film in store.films">
                {{ film.name }}
                {{ film.original_name }}
                <!-- {{ film.original_language }} -->
                <span class="fi" :class="'fi-'+film.original_language"></span>
                {{ film.vote_count }}
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