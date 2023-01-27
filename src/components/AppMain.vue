<script>
    import {store} from '../store'
    export default {
        data(){
            return {
                store,
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
          <!-- <div>
              {{ movie.original_title }}        
          </div> -->
          <img class="img-fluid flag" :src="`/src/assets/img/${movie.original_language}.png`">  
          <div>

            <div class="empty-star">
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              
              <div class="full-star">
                <i v-for="n in Math.ceil(movie.vote_average / 2)" class="fa-solid fa-star"></i>
              </div>
              
            </div>

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

          <div class="empty-star">
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              
              <div class="full-star">
                <i v-for="n in Math.ceil(serie.vote_average / 2)" class="fa-solid fa-star"></i>
              </div>    
            </div>

        </li>
      </ul>
    </div>


</template>


<style>
  .empty-star {
    position: relative;
  }

  .full-star {
    position: absolute;
    top: 0;
  }

  
</style>