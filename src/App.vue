<script>
import axios from 'axios'
import {store} from './store'
export default {
  data (){
    return {
      store,
      searchProduct: '',
      apiUri: 'https://api.themoviedb.org/3/search/movie?api_key=a98e974a1dcb89c6e968d61b061b2de8&query=all',
      movies: [],
      series: []
      
    }
  },
  methods: {
      fetchMovie(url) {
        axios.get(url)
        .then((res) => {
        this.movies = res.data.results;
      });
      },

      fetchSeries(url) {
        axios.get(url)
        .then((res) => {
        this.series = res.data.results;
      });
      },

      onTypeSearch(){
        const movieUri = `https://api.themoviedb.org/3/search/movie?api_key=a98e974a1dcb89c6e968d61b061b2de8&query=${this.searchMovie}`
        this.fetchMovie(movieUri);

        const seriesUri = `https://api.themoviedb.org/3/search/tv?api_key=a98e974a1dcb89c6e968d61b061b2de8&query=${this.searchMovie}`
        this.fetchSeries(seriesUri)
      },

      cleanInput(){
        if (this.searchMovie === ''){
          this.movies = []
          this.series = []
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
    <div class="movies">
      <h1>Movies</h1>
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
    </div>

    <div class="series">
      <h1>Series</h1>
      <ul>
        <li v-for="serie in series">
          <div>
              {{ serie.name }}        
          </div>
          <div>
              {{ serie.original_name }}        
          </div>
          <img class="img-fluid flag" :src="`/src/assets/img/${serie.original_language}.png`">  
          <div>
              {{ serie.vote_average }}        
          </div>
        </li>
      </ul>
    </div>


</template>


<style> 
  .flag {
    height: 25px;
    width: 35px;
  }
</style>