<script setup lang="ts">
import { ref } from 'vue'


const props = withDefaults(defineProps<{
  title: string;
  category: string;
  description: string;
  image: string;
  price: string;
  rating: {
    rate: number | string,
    count: number| string,
  };
}>(), {
    category: 'common',
});

</script>

<template>
  <li
  class="product-card"
  >
  <p class="product-card__category">{{category}}</p>
  <h4 class="product-card__title">{{title}}</h4>
  <div class="product-card__image">
    <img :src="image" :alt="title">
  </div>
  <div class="product-card__row">
    <p class="product-card__rating.rate">{{rating?.rate}}</p>
    <p class="product-card__price">{{price}}</p>
  </div>
  <p class="product-card__description">{{description}}</p>


  </li>
</template>

<style scoped  lang="scss">
.product-card {
    display: flex;
    flex-direction: column;
    max-width: 24%;
    padding: 8px;
    border: 1px solid #424242;
    border-radius: 12px;

    &__image {
        height: 300px;
        width: 200px;
        align-self: center;

        img {
            object-fit: cover;
        }
    }

    &__row {
        display: flex;
        justify-content: space-between;
    }

}
</style>
