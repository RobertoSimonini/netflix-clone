<script>
export default {
    name: 'ProductCard',
    props: {
       product: Object
    }
}

</script>



<template>
        <main>
            <figure>
                <img :src="`https://image.tmdb.org/t/p/w342/${product.poster_path}`" :alt="product.title">
            </figure>
            <div>
                  {{ product.title || product.name }}        
            </div>
            <div>
                  {{ product.original_title || product.original_name }}        
            </div>
            <img class="img-fluid flag" :src="`/src/assets/img/${product.original_language}.png`">
            
            
    
            <div>
                <!-- Qui metto le stelle vuote che saranno riemptive assolutamente e dinamicamente da quelle piene  -->
                <div class="empty-star">
                    <i class="fa-regular fa-star"></i>
                    <i class="fa-regular fa-star"></i>
                    <i class="fa-regular fa-star"></i>
                    <i class="fa-regular fa-star"></i>
                    <i class="fa-regular fa-star"></i>
                  
                    <div class="full-star">
                        <i v-for="n in Math.ceil(product.vote_average / 2)" class="fa-solid fa-star"></i>
                    </div>
                </div>
            </div>
        </main>

</template>



<style lang="scss" scoped>
    .empty-star {
    position: relative;
  }

  .full-star {
    position: absolute;
    top: 0;
    color: gold;
  }
</style>

