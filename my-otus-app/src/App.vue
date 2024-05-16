<script setup lang="ts">
import ProductCard from './components/ProductCard.vue';
import { ref } from 'vue';

const products = ref(null);

fetch('https://fakestoreapi.com/products')
    .then(response => response.json())
    .then(data => products.value = data);

console.log(products);
</script>

<template>
  <div>
    <h1>Каталог</h1>
    <ul class="products__list">
      <ProductCard
        v-for="product in products"
        :key="product.id"
        :category="product.category"
        :description="product.description"
        :image="product.image"
        :price="product.price"
        :rating="product.rating"
        :title="product.title"
      />
    </ul>
  </div>
</template>

<style scoped lang="scss">
@import "./style.scss";

.products {

  &__list {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    flex-wrap: wrap;
    height: auto;
    gap: 8px
  }
}

</style>
