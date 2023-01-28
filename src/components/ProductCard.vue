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
    <div class="product-card" v-if="product.poster_path">
        <figure>
            <img class="card-cover" :src="`https://image.tmdb.org/t/p/w342/${product.poster_path}`" :alt="product.title">

            <div class="content h-100 w-100 d-flex flex-column p-3">
                <div>
                    <h3>
                        Titolo: {{ product.title || product.name }}        
                    </h3>
                    <h4>
                       Titolo originale: {{ product.original_title || product.original_name }})        
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
            width: 20vw;
            height: 650px;
    }

    .content {
            position: absolute;
            top: 0;
            left: 0;
            color: white;
            opacity: 0;
            transition: 0.25s;

        *{
            padding: 10px 0;
        }
    }

    }

.product-card {
    flex-basis: 25%;
    overflow-y: hidden;
    cursor: pointer;

}


.product-card:hover .content {
    background-color: rgba(black, 0.75);
    overflow-y: scroll;
    opacity: 1;

}


.flag {
    height: 45px;
    width: 50px;
}


.empty-star {
    position: relative;
}

.full-star {
    position: absolute;
    top: 0;
    color: gold;
}


</style>

