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
    },
    computed: {
        title (){
            return this.product.title || this.product.name;
        },
        originalTitle (){
            return this.product.original_title || this.product.original_name;
        },
        roundedVote (){
            return Math.ceil(this.product.vote_average / 2);
        },
        overView (){
            return this.product.overview;
        }
    }
}

</script>



<template>
    <div class="card-wrapper" v-if="product.poster_path">
        <div class="product-card">
            <img class="card-cover" :src="`https://image.tmdb.org/t/p/w342/${product.poster_path}`" :alt="product.title">
            
            <div class="content h-100 w-100 d-flex flex-column p-3">
                <div>
                    <h3>
                        Titolo: {{ title }}        
                    </h3>
                    <h4>
                        Titolo originale: {{ originalTitle }}   
                    </h4>
                </div>
                <img class="img-fluid flag" :src="`/src/assets/img/flags/${product.original_language}.png`">
                
                <div>
                    <!-- Qui metto le stelle vuote che saranno riemptive assolutamente e dinamicamente da quelle piene  -->
                    <div class="empty-star">
                        <i v-for="n in 5" class="fa-regular fa-star"></i>
                        
                        
                        <div class="full-star">
                            <i v-for="n in roundedVote" class="fa-solid fa-star"></i>
                        </div>     
                    </div>
                    
                    <div class="overview">
                        <h3> Trama: </h3>
                        <p>
                            {{ overView }}
                        </p>           
                    </div>
                    
                </div>
            </div>
        </div>
    </div>
        
</template>



<style lang="scss" scoped>

.card-wrapper {
    flex-basis: 25%;
    position: relative;
    width: 25vw;
    height: 600px;
}


.product-card {
    position: absolute;
    width: 97.5%;
    height: 100%;
    transform-style: preserve-3d;
    transition: transform 0.5s;
    transition-delay: 0.25s;
    
}

.product-card:hover{
    cursor: grabbing;
    transform: rotateY(180deg);
}

.card-cover {
    position: absolute;
    width: 97.5%;
    height: 100%;
    backface-visibility: hidden;

}

.content {
            cursor: auto;
            position: absolute;
            width: 97.5%;
            height: 100%;
            backface-visibility: hidden;
            transform: rotateY(180deg);

            color: white;
            background-color: black;
            overflow-y: auto;


        *{
            padding: 10px 0;
        }

        .overview{
            padding: 0;

            h3{
                padding-bottom: 0;
            }

            p {
                padding-top: 0;
            }
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

