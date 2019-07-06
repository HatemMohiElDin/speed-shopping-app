<template>
  <div class="container">
    <slot name="veggie"></slot>
  </div>

  <!-- <h3>Veggies and fruit</h3>
    
<table>
        <tr v-for="product in userVeggie" :key="product.id">
            <td > {{product}} </td> <td><app-counter></app-counter></td>
        </tr>
    </table>    
  </div>-->
</template>

<script>
import Counter from "./Counter";

export default {
  props: {
    userVeggie: Array
  },
  components: {
    appCounter: Counter
  }
};
</script>

<style scoped>
@import "../assets/styles/products.css";
</style>


