<script>
import axios from 'axios'
import {store} from './store'
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'
export default {
  components : {AppHeader, AppMain},

  data (){
    return {
      store,
      apiUri: 'https://api.themoviedb.org/3/search/movie?api_key=a98e974a1dcb89c6e968d61b061b2de8&query=all',
      
    }
  },

  methods: {
      fetchMovie(url) {
        axios.get(url)
        .then((res) => {
        store.movies = res.data.results;
      });
      },

      fetchSeries(url) {
        axios.get(url)
        .then((res) => {
        store.series = res.data.results;
      });
      },

      onProductSearch(searchProduct){
        const movieUri = `https://api.themoviedb.org/3/search/movie?api_key=a98e974a1dcb89c6e968d61b061b2de8&query=${searchProduct}`
        this.fetchMovie(movieUri);

        const seriesUri = `https://api.themoviedb.org/3/search/tv?api_key=a98e974a1dcb89c6e968d61b061b2de8&query=${searchProduct}`
        this.fetchSeries(seriesUri)
      },

      cleanInput(searchProduct){
        if (searchProduct === ''){
          store.movies = []
          store.series = []
        }
      }
  },
}
</script>




<template>
 <app-header @product-search="onProductSearch" @clean-input="cleanInput"></app-header>

  
    <div class="movies">
      <h1>Movies:</h1>
      <ul> 
        <li v-for="movie in store.movies">
          <figure>
            <img :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" alt="">
          </figure>
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
      <h1>Series:</h1>
      <ul>
        <li v-for="serie in series">
          <figure>
            <img :src="`https://image.tmdb.org/t/p/w342/${serie.poster_path}`" alt="">
          </figure>
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

  ul {
    list-style-type: none;
  }

</style>