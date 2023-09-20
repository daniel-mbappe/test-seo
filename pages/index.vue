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

useHead({
  title: 'Nuxt: The Ultimate SEO Test',
  meta: [
    {
      name: 'description',
      content: 'Build your next SEO Vue.js application with confidence using Nuxt 3....' 
    },
    {
      name: 'google-site-verification',
      content: 'EQsvJzHHiOYUjjBQPp99Okpz61pH3ozPfxsrNu4IpfU' 
    },
  ],
  link: [
    {
      hid: 'canonical',
      rel: 'canonical',
      href: 'https://test-seo-ten.vercel.app',
    }
  ],
})

useSeoMeta({
  // title: 'Nuxt: The Ultimate SEO Test',
  // ogTitle: 'Nuxt: The Ultimate SEO Test',
  // description: "Passionnés par les entrepreneurs, nous investissons dans des projets qui changent la société. Si tel est votre cas, partagez-nous votre vision et dites-nous ce qui vous anime. Nous serions ravis de vous accompagner.",
  // ogDescription: "Passionnés par les entrepreneurs, nous investissons dans des projets qui changent la société. Si tel est votre cas, partagez-nous votre vision et dites-nous ce qui vous anime. Nous serions ravis de vous accompagner.",
  // ogImage: '',
  // twitterCard: '',
  robots: {
    index: true,
    follow: true,
  }
})
</script>