<template>
  <div>
    <div class="productContainer">
      <div class="product" v-for="(product, i) in data" :key="i">
        <RouterLink :to="`/catalog/becos_article_${product.id}`">
          <div>
            {{  product.title  }}
          </div>
        </RouterLink>
        <div>{{ product.description }}</div>
      </div>
    </div>
  </div>
</template>

<script setup>
const data = await fetch('https://dummyjson.com/products')
  .then(res => res.json())
  .then(data => data.products)
</script>