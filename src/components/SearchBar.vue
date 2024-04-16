<template>
    <div>
        <input type="text" placeholder="Cerca il tuo Film" v-model="ascolto">
        <button @click="getMovie(), getFilm()">Cerca</button>
    </div>
    <div>
        <ul>
            <li v-for="movie in movies">
                {{ movie.title }}
                {{ movie.original_title }}
                <!-- {{ film.original_language }} -->
                <span class="fi" :class="'fi-'+movie.original_language"></span>
                {{ movie.vote_count }}
            </li>
            <li v-for="film in films">
                {{ film.name }}
                {{ film.original_name }}
                <!-- {{ film.original_language }} -->
                <span class="fi" :class="'fi-'+film.original_language"></span>
                {{ film.vote_count }}
            </li>
        </ul>
        <!-- <ul></ul> -->
    </div>
</template>

<script>
    import "/node_modules/flag-icons/css/flag-icons.min.css"
    import axios from 'axios'
    export default {
        data() {
            return {
                API_KEY: '7057874650184c3732f30fe5528a0e6d',
                ascolto: '',
                films: [],
                movies: [],

            }
        },
        methods: {
            getMovie() {
                axios.get('https://api.themoviedb.org/3/search/movie', {
                    params: {
                        api_key: this.API_KEY,
                        query: this.ascolto

                    }
                })
                .then((res) => {
                    // console.log(res.data.results)

                    for(let i = 0; i < res.data.results.length; i++) {
                        const results = res.data.results[i]
                        this.movies.push(results)
                    }
                    // console.log(this.films)
                    // console.log(this.films.title)

                })
            },
            getFilm() {
                axios.get('https://api.themoviedb.org/3/search/tv', {
                    params: {
                        api_key: this.API_KEY,
                        query: this.ascolto

                    }
                })
                .then((res) => {
                    console.log(res.data.results)

                    for(let i = 0; i < res.data.results.length; i++) {
                        const results = res.data.results[i]
                        this.films.push(results)
                    }
                    // console.log(this.films)
                    // console.log(this.films.title)

                })
            }
        },
        // mounted() {
        //     console.log(this.getFilm())
        // }
    }

</script>

<style lang="scss" scoped>
// .fi {
//     background-size: contain;
//     background-position: 50%;
//     background-repeat: no-repeat;
// }
</style>