<template>
  <div>
    <h1>Products</h1>
    <div>
      <ul>
        <li v-for="(product, index) in products" :key="index">
          <NuxtLink :to="product.slug.current"> {{ product.title }}</NuxtLink>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { groq } from "@nuxtjs/sanity";
export default {
  async asyncData({ $sanity }) {
    const query = groq`*[_type == "product"]`;
    const products = await $sanity.fetch(query);
    return { products };
  },
};
</script>
<style scoped>
ul {
  list-style-type: none;
}
ul li {
  padding: 0.3rem 0;
}
ul li a {
  text-decoration: none;
  color: rgb(27, 27, 27);
}
</style>