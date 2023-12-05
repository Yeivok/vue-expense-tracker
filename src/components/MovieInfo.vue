

<template>
    

    <div v-if="movie">
    <h1>{{ movie.title }}</h1>
    <img :src="'https://image.tmdb.org/t/p/w300'+movie.poster_path" width="300">
    <p>{{ movie.tagline }}</p>

    <h3>Estreno</h3>
    <p>{{ movie.release_date }}</p>
    <h3>Duracion</h3>
    <p>{{ movie.runtime }} min</p>
    <h3>Calificación</h3>
    <p>{{ movie.vote_average }} </p>

    <h3>Sinopsis</h3>
    <p>{{ movie.overview }}</p>

    <h6 v-if="movie.homepage">
        <a href="movie.homepage" target="_blank">Pagina oficial</a>
    </h6>
    </div>
    <div v-else>Cargando...</div>

</template>

<script>
    import axios from 'axios'

    export default{
        name:"MovieInfo",
        components:{
            
        },
        methods:{
      MovieList(){
        this.$router.push("/movie/" + this.movie.id)
      }
      
    },
        data(){
            return{
                movie:null,
            }
        },
        async mounted (){
        await axios.get('https://api.themoviedb.org/3/movie/'+this.$route.params.id+'?language=es-MX&api_key=609dfb4689b86f930ab28d5c11f3f090')
            .then((res)=>{
            console.log(res.data)
            this.movie=res.data
            })
            .catch((err)=>{
            console.log(err)
    })
    }
        
    }
</script>
