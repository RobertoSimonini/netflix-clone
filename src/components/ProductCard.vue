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
                <img class="img-fluid flag" :src="`/src/assets/img/flags/${product.original_language}.png`">
                
                <div>
                    <!-- Qui metto le stelle vuote che saranno riemptive assolutamente e dinamicamente da quelle piene  -->
                    <div class="empty-star">
                        <i v-for="n in 5" class="fa-regular fa-star"></i>
                        
                        
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

.product-card {
    flex-basis: 23%;
    position: relative;
    width: 20vw;
    height: 650px;
    margin: 1rem;
}


figure {
    position: absolute;
    cursor: pointer;
    width: 100%;
    height: 100%;
    transform-style: preserve-3d;
    transition: transform 0.5s;
    transition-delay: 0.25s;
    
}

figure:hover{
    transform: rotateY(180deg);
}

.card-cover {
    position: absolute;
    width: 100%;
    height: 100%;
    backface-visibility: hidden;

}

.content {
            position: absolute;
            width: 100%;
            height: 100%;
            backface-visibility: hidden;
            transform: rotateY(180deg);

            color: white;
            background-color: black;
            overflow-y: auto;


        *{
            padding: 10px 0;
        }
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

