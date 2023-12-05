<template>
    <h1>Buscale estan chidas</h1>
  <input type="text" placeholder=" Buscar pelicula" v-model="search" v-on:keyup.enter="searchData">
  <Movies v-for="movie in movies" v-bind:key="movie.idMeal" v-bind:movie="movie"/>
  <h1>CATEGORIAS</h1>
  <Category 
  v-for="category in paginated"
  v-bind:key="category.idCategory"
  v-bind:category="category"
  />
  <div class="text-center">Actual {{ current }}</div>
  <div class="text-center">
    <a @click="$event=>prev()">Anterior</a>
    <a @click="$event=>next()">Siguiente</a>
  </div>
</template>

<script>
import Category from './Category.vue'
import Movies from './Movies.vue'
import swal from 'sweetalert'
import axios from 'axios'

export default{
  name:'App',
  data(){
    return{
      categories:[], //lo llenaremos con la api
      current:1,
      pageSize:5,
      search:'',
      movies:[]

    }
  },
  mounted(){
    axios.get('https://api.themoviedb.org/3/genre/movie/list?language=es&api_key=609dfb4689b86f930ab28d5c11f3f090')
    .then((res)=>{
      this.categories=res.data.genres
    })
    .catch((err)=>{
      console.log(err)
    })
  },
  components:{
    Category,
    Movies,
  },

  computed:{
    indexStart(){
      return (this.current-1)*this.pageSize
    },
    indexEnd(){
      return this.indexStart+this.pageSize
    },
    paginated(){
      return this.categories.slice(this.indexStart, this.indexEnd)
    }
  }, 
  methods:{
    prev(){
      this.current--
    },
    next(){
      this.current++
    },
    searchData(){
      if(this.search){
        axios.get('https://api.themoviedb.org/3/search/movie?language=es-MX&query='+this.search+'&api_key=609dfb4689b86f930ab28d5c11f3f090')
        .then((res)=>{
          console.log(res)
          this.movies=res.data.results
        })
      }else{
        //alert("buscando...")
        swal({
    title: "Atencion",
    text: "Ingresa un nombre para continuar",
    icon: "warning",
  });
      }
    }
  }
}
</script>