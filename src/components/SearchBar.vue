<template>
    <div>
        <input type="text" placeholder="Cerca il tuo Film" v-model="ascolto">
        <button @click="getFilm()">Cerca</button>
    </div>
    <div>
        <ul>
            <li v-for="film in films">
                {{ film.title }}
                {{ film.original_title }}
                {{ film.original_language }}
                {{ film.vote_count }}
            </li>
        </ul>
    </div>
</template>

<script>
    import axios from 'axios'
    export default {
        data() {
            return {
                API_KEY: '7057874650184c3732f30fe5528a0e6d',
                ascolto: '',
                films: [],
                titles: [],
                originalTitles: [],
                languages: [],
                votes: []

            }
        },
        methods: {
            getFilm() {
                axios.get('https://api.themoviedb.org/3/search/movie', {
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
                    console.log(this.films)
                    console.log(this.films.title)

                })
            }
        },
        // mounted() {
        //     console.log(this.getFilm())
        // }
    }

</script>

<style lang="scss" scoped>

</style>