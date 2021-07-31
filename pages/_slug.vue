<template>
  <div>
    <h1>Product</h1>
    <p>{{ product.title }}</p>
    <p>{{ product.blurb.en }}</p>
  </div>
</template>

<script>
import { groq } from "@nuxtjs/sanity";
export default {
  async asyncData({ params, $sanity }) {
    const query = groq`*[_type == "product" && slug.current == "${params.slug}"][0]`;
    const product = await $sanity.fetch(query);
    return { product };
  },
};
</script>

<style  scoped>
</style>