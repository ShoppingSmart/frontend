<template>
  <div class="overflow-y-hidden">
    <div class="2xl:container 2xl:mx-auto">
      <div class="lg:px-20 md:px-6 px-4 md:py-12 py-8">
        <div class="flex justify-between items-center">
          <h1 class="text-3xl lg:text-4xl font-semibold text-gray-800 text-left">Categories</h1>
          <nuxt-link to="/categories/create">
            <SharedMoreButton></SharedMoreButton>
          </nuxt-link>
        </div>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 lg:gap-8 mt-8 md:mt-10">
          <nuxt-link v-for="{ name, image, tax } in categories" to="#">
            <CardItem :name="name" :image="image">
              <span>Tax: {{ tax }}%</span>
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
    const { data } = await axios.get(`${this.$config.APP_URL}/v1/categories`);
    this.categories = data;
  },
};
</script>
