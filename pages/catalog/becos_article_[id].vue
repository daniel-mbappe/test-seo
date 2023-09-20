<template>
  <div class="details">
    <img :src="productDetails.thumbnail" :alt="productDetails.title">
    <h2>
      {{ productDetails.title }}
    </h2>
    <div>
      {{ productDetails.description }}
    </div>
  </div>
</template>

<script setup>
const { path } = useRoute()
const route = useRoute();
const itemId = route.params.id
const baseUrl = 'https://test-seo-ten.vercel.app';
const canonicalPath = baseUrl + (path + '/').replace(/\/+$/, '/') + '/';
const productDetails = await fetch(`https://dummyjson.com/products/${itemId}`).then(res => res.json()).then(data => data);
const title = `${productDetails.title} | ${productDetails.description}`;

useHead({
  title: title,
  meta: [
    {
      name: 'description',
      content: productDetails.description
    },
  ],
  link: [
    {
      hid: 'canonical',
      rel: 'canonical',
      href: canonicalPath
    }
  ],
})
</script>