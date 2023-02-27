<template>
  <div class="overflow-y-hidden">
    <div class="2xl:container 2xl:mx-auto">
      <div class="lg:px-20 md:px-6 px-4 md:py-12 py-8">
        <div class="flex justify-between items-center">
          <h1 class="text-3xl lg:text-4xl font-semibold text-gray-800 text-left">Categories</h1>
          <nuxt-link to="/categories/create">
            <div class="w-auto h-auto cursor-pointer">
              <div class="flex-1 h-full">
                <div class="flex items-center justify-center flex-1 h-full p-2 bg-green-500 text-white shadow rounded-full">
                  <div class="relative">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6m0 0v6m0-6h6m-6 0H6" />
                    </svg>
                  </div>
                </div>
              </div>
            </div>
          </nuxt-link>
        </div>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 lg:gap-8 mt-8 md:mt-10">
          <nuxt-link v-for="{ name, image } in categories" to="#">
            <div class="bg-gray-50 p-8 transform transition duration-500 hover:scale-110 border-2 rounded-md hover:border-gray-500">
              <h2 class="text-xl text-gray-800 font-semibold">{{ name }}</h2>
              <div class="flex justify-center items-center mt-4 md:mt-19">
                <img class="w-full h-52" :src="image" :alt="name" role="img" />
              </div>
            </div>
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
    const { config, data, headers, request, status, statusText } = await axios.get("http://127.0.0.1:8888/api/v1/categories");

    this.categories = data;
  },
};
</script>
