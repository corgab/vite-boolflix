<template>
    <div class="flex">
        <img src="https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" alt="">
        <div>
            <input type="text" placeholder="Cerca il tuo Film" v-model="store.query">
            <button @click="getMovie(), getFilm(), getMovieGenres()">Cerca</button>
        </div>
    </div>
</template>

<script>
import "/node_modules/flag-icons/css/flag-icons.min.css"
import { store } from '../store.js'
import axios from 'axios'
export default {
    data() {
        return {
            store,
        }
    },
    methods: {
        getMovie() {
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: this.store.API_KEY,
                    query: this.store.query

                }
            })
                .then((res) => {

                    for (let i = 0; i < res.data.results.length; i++) {
                        const result = res.data.results[i]
                        this.store.movies.push(result)
                    }

                })
        },
        getFilm() {
            axios.get('https://api.themoviedb.org/3/search/tv', {
                params: {
                    api_key: this.store.API_KEY,
                    query: this.store.query

                }
            })
                .then((res) => {

                    for (let i = 0; i < res.data.results.length; i++) {
                        const results = res.data.results[i]
                        this.store.films.push(results)
                    }
                    // console.log(res.data.results)

                })
        },
        getMovieGenres() {
            axios.get('https://api.themoviedb.org/3/genre/movie/list', {
                params: {
                    api_key: this.store.API_KEY,
                }
            })
                .then((res) => {
                    console.log(res.data)
                    for(let i = 0; i < res.data.genres.length; i++) {
                        this.store.moviesGenres.push(res.data.genres[i])
                        console.log(res.data.genres[i])
                    }
                    console.log(this.store.moviesGenres)
                })
        }
    },
}

</script>

<style lang="scss" scoped>
.flex {
    justify-content: space-between;
    align-items: center;
    padding-top: 20px;
}
img {
    width: 200px;
}
</style>
