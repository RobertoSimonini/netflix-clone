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
  },

  created() {
    this.fetchMovie(this.apiUri);
  }
}
</script>




<template>
  <h1 class="text-danger">
    Hello Boolflix
  </h1>

  <div class="input-group flex-nowrap w-25">
    <input v-model="searchMovie" type="text" class="form-control" placeholder="Username" aria-label="Username" aria-describedby="addon-wrapping">
  </div>

  <ul>
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