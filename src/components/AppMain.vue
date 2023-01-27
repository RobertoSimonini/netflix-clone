<script>
    import {store} from '../store'
    import ProductCard from './ProductCard.vue'
    export default {
      name: 'Appmain',
        data(){
            return {
                store,
            }
        },   
        components: {ProductCard}
        }
</script>


<template>
    <div class="movies">
      <h1>Movies:</h1>
          <product-card v-for="movie in store.movies" v-bind="movie"></product-card>
    </div>

    <div class="series">
      <h1>Series:</h1>
          <product-card v-for="serie in store.series"  v-bind="serie"></product-card>
    </div>


</template>


<style>
  .empty-star {
    position: relative;
  }

  .full-star {
    position: absolute;
    top: 0;
    color: gold;
  }

  
</style>