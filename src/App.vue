<script>
import axios from 'axios'
import {store} from './store'
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'
export default {
  name: 'App',
  components : {AppHeader, AppMain},

  data (){
    return {
      store,
      baseUri: 'https://api.themoviedb.org/3',
      apiKey: 'api_key=a98e974a1dcb89c6e968d61b061b2de8'
      
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
        const movieUri = `${this.baseUri}/search/movie?${this.apiKey}&query=${searchProduct}`
        this.fetchMovie(movieUri);

        const seriesUri = `${this.baseUri}/search/tv?${this.apiKey}&query=${searchProduct}`
        this.fetchSeries(seriesUri)
      },

      cleanInput(searchProduct){
        if (searchProduct === ''){
          store.movies = []
          store.series = []
          return
        }
      }
  },
}
</script>




<template>
    <app-header @product-search="onProductSearch" @clean-input="cleanInput"></app-header>
    <app-main></app-main>

  
    

</template>


<style>
    
  ul {
    list-style-type: none;
  }

</style>