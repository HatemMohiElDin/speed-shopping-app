<template>
<div class="container">
    <h3>Bread and Pastries</h3>
    <table>
        <tr v-for="(product, index) in userBread" :key="product.id">
            <td > {{product}}<button @click="deleteItem" class="btn btn-primary btn-sm">  X </button></td> <td><app-counter></app-counter></td>
        </tr>
    </table>
     
    </div>
</template>

<script>
import Counter from './Counter'


export default {
    props:{
        userBread:Array
    },
    components:{
        appCounter:Counter,
    },
    methods:{
        deleteItem(index){
            this.userBread.splice(index,1)
        }
    }

    
    
    
 
}
</script>

<style scoped>
@import '../assets/styles/products.css';


button{
    margin-left: 10px;
}

</style>


