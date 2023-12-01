<script setup>
import ChildComponent from './components/ChildComponent.vue'
import { ref } from 'vue';
import axios from 'axios';

const products = ref(null);
const selectedProduct = ref(null);

  axios.get('https://jsonplaceholder.typicode.com/todos')
  .then(response => {
    products.value = response.data;
    console.log('Fetched data:', response.data);
  })
  .catch(error => {
    console.error('Error fetching data:', error);
  });

  const sendToChild = (product) => {
  selectedProduct.value = product;
};

</script>

<template>
  <div>
    <ChildComponent
      v-if="selectedProduct"
      :userId="selectedProduct.id"
      :title="selectedProduct.title"
      :completed="selectedProduct.completed"
    />

    <span class='heading'>Fetch Api</span>
    <ul>
      <li v-for="product in products" :key="product.id">
        <span>{{ product.id }}</span>
        <span>{{ product.title }}</span>
        <span>{{ product.completed}}</span>
         <button @click="sendToChild(product)">Share Data with child component</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.heading {
  text-align: center;
}
</style>
