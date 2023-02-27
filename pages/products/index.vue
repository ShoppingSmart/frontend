<template>
  <div class="overflow-y-hidden">
    <div class="2xl:container 2xl:mx-auto">
      <div class="lg:px-20 md:px-6 px-4 md:py-12 py-8">
        <div class="flex justify-between items-center">
          <h1 class="text-3xl lg:text-4xl font-semibold text-gray-800 text-left">Products</h1>
          <nuxt-link to="/products/create">
            <SharedMoreButton></SharedMoreButton>
          </nuxt-link>
        </div>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 lg:gap-8 mt-8 md:mt-10">
          <nuxt-link v-for="{ name, image, price } in categories" to="#">
            <CardItem :name="name" :image="image">
              <span>Price: ${{ price / 100 }}</span>
            </CardItem>
          </nuxt-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      categories: [],
    };
  },
  async created() {
    const { data } = await axios.get("http://127.0.0.1:8888/api/v1/products");

    this.categories = data;
  },
};
</script>
