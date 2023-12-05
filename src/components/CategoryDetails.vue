

<template>
    

    <h3>Lista de peliculas {{ category_title }}</h3>
    <Movies v-for="movie in movies" v-bind:key="movie.id" v-bind:movie="movie"/>
</template>

<script>
    import axios from 'axios'
    import Movies from './Movies.vue'
    export default{
        name:"CategoryDetails",
        components:{
            Movies,
        },
        data(){
            return{
                category_title:this.$route.params.title,
                movies:[],
                page:1, 
                pages:1,
            }
        },
        mounted(){
        axios.get('https://api.themoviedb.org/3/discover/movie?include_adult=false&include_video=false&language=es-MX&page=1&primary_release_year=2023&with_genres='+this.$route.query.id+'&api_key=609dfb4689b86f930ab28d5c11f3f090')
        .then((res)=>{
            this.movies=res.data.results
            })
            .catch((err)=>{
            console.log(err)
    })
    }
        
    }
</script>
