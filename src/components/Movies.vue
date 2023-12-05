<template>
    <div class="category-container">
        <img @click="MovieList" :src="'https://image.tmdb.org/t/p/w500'+movie.poster_path" alt="">
        <h3>{{ movie.title }}</h3>
        <p>Sinopsis: {{ movie.overview }} </p>
    </div>
</template>


<script>
export default{
    props:["movie"],
    methods:{
      MovieList(){
        //console.log(this.category)
        this.$router.push("/movie/" + this.movie.id)
        //console.log(this.meal.idMeal)
      }
      
    },
}

</script>