<script>
import {store} from '../store'
export default {
    name: 'AppHeader',
    data () {
        return {
            store,
            searchProduct: '',
        }
    },
    methods: {
        
    },
    emits: ['product-search', 'clean-input']
}
</script>










<template>
    <header class="d-flex justify-content-between align-items-center">
        <h1 class="text-danger">
            BOOLFLIX
        </h1>
    
        <div class="input-group flex-nowrap w-25">
            <input @keyup="$emit('clean-input', searchProduct)" @keyup.enter="$emit('product-search', searchProduct)" v-model.trim="searchProduct" type="text" class="form-control" placeholder="Search a Product">
            <button @click="$emit('product-search', searchProduct)" class="btn btn-danger">Cerca</button>
        </div>
    </header>

</template>







<style scoped>
    header {
        padding: 0 7.5%;
        height: 100px;
        background-color: black;
    }
</style>