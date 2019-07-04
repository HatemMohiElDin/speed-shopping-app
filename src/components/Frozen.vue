<template>
<div class="container">
    <h3>Frozen section</h3>
    <table>
        <tr v-for="product in userFrozen" :key="product.id">
            <td > {{product}} </td> <td><app-counter></app-counter></td>
        </tr>
    </table>
    </div>
</template>

<script>
import Counter from './Counter'


export default {
    props:{
        userFrozen:Array
    },
    components:{
        appCounter:Counter,
    }
    
    
    
 
}
</script>

<style scoped>
@import '../assets/styles/products.css';

</style>


