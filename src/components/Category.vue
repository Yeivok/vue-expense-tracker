
<template>
  <div @click="openCategoryList" class="category-container" >
  <h3>{{category.name}}</h3>
  </div>
  
  </template>
  
  <script>
  export default{
    props:["category"],
    methods:{
      openCategoryList(){
        console.log(this.category)
        this.$router.push("/category/" + this.category.name+"?id="+this.category.id)
        //console.log(this.category.strCategory)
      }
      
    }
  }
  </script>