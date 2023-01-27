<script>
export default {
    name: 'ProductCard',
    props: {
       product: Object
    },
    data (){
        return {
            hover: false
        }
    }
}

</script>



<template>
    <div class="product-card">
        <figure  @mouseover="hover = true" @mouseleave="hover = false">
            <img class="card-cover" :src="`https://image.tmdb.org/t/p/w342/${product.poster_path}`" :alt="product.title">

            <div v-if="hover" class="content h-100 w-100 d-flex flex-column align-items-center p-3">
                <div>
                    <h2>
                        {{ product.title || product.name }}        
                    </h2>
                    <h4>
                       ({{ product.original_title || product.original_name }})         
                    </h4>
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

                    <div>
                        <h3> Trama </h3>
                        <p>
                            {{ product.overview }}
                        </p>           
                    </div>

                </div>
            </div>

        </figure>   
    </div>

</template>



<style lang="scss" scoped>

    figure {
        position: relative;
       

        .card-cover {
            max-width: 20vw;
            height: 600px;
        }

        .content {
            position: absolute;
            top: 0;
            left: 0;
            color: white;
            background-color: black;
            overflow-y: auto;
            overflow-x: hidden;

            *{
                padding: 10px 0;
            }
        }
    }

.empty-star {
    position: relative;
}

.full-star {
    position: absolute;
    top: 0;
    color: gold;
}

  .product-card {
    flex-basis: 25%;
    cursor: pointer;
  }
</style>

