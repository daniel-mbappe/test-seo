<template>
  <div class="flex flex-col p-4">
    <div class="grid grid-cols-8 gap-2">
      <div v-for="(product, i) in data" :key="i">
        <RouterLink :to="`/catalog/becos_article_${product.id}`">
          <div class="flex flex-col border border-black rounded-[8px] p-2 gap-4">
            <p class="text-xl">
              {{ product.title }}
            </p>

            <p class="text-xs">{{ product.description }}</p>
          </div>
        </RouterLink>
      </div>
    </div>
  </div>
</template>

<script setup>
const data = await fetch('https://dummyjson.com/products')
  .then(res => res.json())
  .then(data => data.products)
</script>