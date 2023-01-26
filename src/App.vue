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
      },

      cleanInput(){
        if (this.searchMovie === ''){
          this.movies = []
        }
      },
  },
}
</script>




<template>
  <h1 class="text-danger">
    Boolflix
  </h1>

  <div class="input-group flex-nowrap w-25">
    <input @keyup="cleanInput" @keyup.enter="onTypeSearch" v-model.trim="searchMovie" type="text" class="form-control" placeholder="Search a Movie" aria-label="Username" aria-describedby="addon-wrapping">
    <button @click="onTypeSearch" class="btn btn-success">Search</button>
  </div>

  <ul> 
    <li v-for="movie in movies">
      <div>
          {{ movie.title }}        
      </div>
      <div>
          {{ movie.original_title }}        
      </div>
      <img class="img-fluid flag" :src="`/src/assets/img/${movie.original_language}.png`">  
      <div>
          {{ movie.vote_average }}        
      </div>
    </li>
  </ul>

</template>


<style> 
  .flag {
    height: 25px;
  }
</style>