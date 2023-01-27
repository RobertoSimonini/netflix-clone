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
  .flag {
    height: 25px;
    width: 35px;
  }

  ul {
    list-style-type: none;
  }

</style>