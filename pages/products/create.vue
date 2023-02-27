<template>
  <div class="overflow-y-hidden">
    <div class="2xl:container 2xl:mx-auto">
      <div class="flex justify-between">
        <div class="mb-4 px-2 w-full">
          <label class="block mb-1 text-sm">Name:</label>

          <input v-model="product.name" class="w-full border px-4 py-2 rounded focus:border-blue-500 focus:shadow-outline outline-none" type="text" autofocus placeholder="Dairy Products" />
        </div>

        <div class="mb-4 px-2 w-full">
          <label class="block mb-1 text-sm">Price ($):</label>

          <input v-model="product.price" type="number" class="w-full border px-4 py-2 rounded focus:border-blue-500 focus:shadow-outline outline-none" min="0" max="100" step="5" />
        </div>
      </div>

      <div class="mb-4 px-2 w-full">
        <label class="block mb-1 text-sm">Select an option</label>
        <select id="countries" v-on:change="onChange" class="border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
          <option selected>Choose a category</option>
          <option v-for="category in categories" :value="category.id">{{ category.name }}</option>
        </select>
      </div>

      <div class="flex justify-between">
        <div class="mb-4 px-2 w-full">
          <label class="block mb-1 text-sm">Image:</label>

          <input v-model="product.image" class="w-full border px-4 py-2 rounded focus:border-blue-500 focus:shadow-outline outline-none" type="text" autofocus placeholder="Link to JPG | PNG image" />
        </div>
      </div>

      <div class="mb-4 px-2 w-full">
        <button v-on:click="submit" class="mx-2 px-4 py-2 text-sm rounded text-white bg-green-500 focus:outline-none hover:bg-green-400">Create</button>

        <nuxt-link to="/products" class="mx-2 px-4 py-2 text-sm rounded text-white bg-blue-500 focus:outline-none hover:bg-blue-400">Back</nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      product: {
        name: "",
        price: 0,
        image: "",
        category_id: 0,
      },
      categories: [],
    };
  },
  async mounted() {
    const { data } = await axios.get("http://127.0.0.1:8888/api/v1/categories");

    this.categories = data;
  },
  methods: {
    onChange($e) {
      this.product.category_id = $e.target.value;
    },
    submit() {
      axios
        .post("http://127.0.0.1:8888/api/v1/products", this.product, {
          headers: {
            "Content-Type": "application/x-www-form-urlencoded",
          },
        })
        .then((response) => {
          alert(`Product created successfully #${response.data.id}`);
        })
        .catch((error) => {
          const message = error.response.data.error;

          alert(message);
        });
    },
  },
};
</script>
