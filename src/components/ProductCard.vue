<script>
export default {
    name: 'ProductCard',
    props: {
        poster_path: String,
        title: String,
        original_title: String,
        original_language: String,
        vote_average: String,

        name: String,
        original_name: String,

    }
}

</script>



<template>

<figure>
            <img :src="`https://image.tmdb.org/t/p/w342/${poster_path}`" :alt="title">
          </figure>
          <div>
              {{ title || name }}        
          </div>
          <div>
              {{ original_title || original_name }}        
          </div>
          <img class="img-fluid flag" :src="`/src/assets/img/${original_language}.png`">  
          <div>


            <!-- Qui metto le stelle vuote che saranno riemptive assolutamente e dinamicamente da quelle piene  -->
            <div class="empty-star">
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              
              <div class="full-star">
                <i v-for="n in Math.ceil(vote_average / 2)" class="fa-solid fa-star"></i>
              </div>
            </div>

          </div>

</template>



<style>
</style>

