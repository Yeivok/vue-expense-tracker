

<template>
  <div>
      <img src="../public/Movie.jpg" class="logo vue" alt="Vue logo" />
  </div>

  <nav id="nav">
    <router-link to="/">Inicio</router-link>
  </nav>
  <router-view></router-view>

  
</template>

<script>
export default{
  name:'App',
  
}
</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #a8adffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #345345aa);
}
.category-container{
  border-radius: 10px;
  color: black;
  margin: 5% 20%;
  background-color: gray;


}
</style>
