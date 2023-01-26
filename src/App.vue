<script>
import axios from 'axios'
import {store} from './store'
export default {
  data (){
    return {
      store,
      searchMovie: '',
      apiUri: 'https://api.themoviedb.org/3/search/movie?api_key=a98e974a1dcb89c6e968d61b061b2de8&query=all',
      movies: []
      
    }
  },
  methods: {
      fetchMovie(url) {
        axios.get(url)
        .then((res) => {
        this.movies = res.data.results;
      });
      },

      onTypeSearch(){
        const apiUri = `https://api.themoviedb.org/3/search/movie?api_key=a98e974a1dcb89c6e968d61b061b2de8&query=${this.searchMovie}`
        this.fetchMovie(apiUri)
      }
  },
}
</script>




<template>
  <h1 class="text-danger">
    Hello Boolflix
  </h1>

  <div class="input-group flex-nowrap w-25">
    <input  @keyup="onTypeSearch" v-model.trim="searchMovie" type="text" class="form-control" placeholder="Search a Movie" aria-label="Username" aria-describedby="addon-wrapping">
  </div>

  <ul v-if="searchMovie"> 
    <li v-for="movie in movies">
      <div>
          {{ movie.title }}        
      </div>
      <div>
          {{ movie.original_title }}        
      </div>
      <div>
          {{ movie.original_language }}        
      </div>
      <div>
          {{ movie.vote_average }}        
      </div>
    </li>
  </ul>

</template>


<style>

</style>