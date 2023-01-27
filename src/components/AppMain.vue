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
    <main class="p-5 d-flex align-items-center justify-content-center">
      <section class="product-container" v-if="store.movies.length || store.series.length">
        <div class="movies">
            <h1 class="text-white">Film</h1>
                <product-card v-for="movie in store.movies" :product="movie" key=""></product-card>
        </div>
    
        <div class="series">
            <h1 class="text-white">Series</h1>
                <product-card v-for="serie in store.series"  :product="serie"></product-card>
        </div>
      </section>

      <h1 v-else class="text-white text-center">
        Prova a cercare un film o una serie TV!
      </h1>
      

    </main>


</template>


<style scoped>
    main {
      background-color: #555555;
      min-height: calc(100vh - 100px);
    }
</style>