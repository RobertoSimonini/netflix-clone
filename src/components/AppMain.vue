<script>
    import {store} from '../store'
    export default {
        data(){
            return {
                store
            }
        },   
        }
</script>


<template>
    <div class="movies">
      <h1>Movies:</h1>
      <ul> 
        <li v-for="movie in store.movies">
          <figure>
            <img :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" :alt="movie.title">
          </figure>
          <div>
              {{ movie.title }}        
          </div>
          <div>
              {{ movie.original_title }}        
          </div>
          <img class="img-fluid flag" :src="`/src/assets/img/${movie.original_language}.png`">  
          <div>
              {{ Math.ceil(movie.vote_average / 2) }}        
          </div>
        </li>
      </ul>
    </div>

    <div class="series">
      <h1>Series:</h1>
      <ul>
        <li v-for="serie in store.series">
          <figure>
            <img :src="`https://image.tmdb.org/t/p/w342/${serie.poster_path}`" :alt="serie.name">
          </figure>
          <div>
              {{ serie.name }}        
          </div>
          <div>
              {{ serie.original_name }}        
          </div>
          <img class="img-fluid flag" :src="`/src/assets/img/${serie.original_language}.png`">
          <div>
              {{ Math.ceil(serie.vote_average / 2)}}        
          </div>
        </li>
      </ul>
    </div>


</template>


<style>

</style>