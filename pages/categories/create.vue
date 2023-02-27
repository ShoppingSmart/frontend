<template>
  <div class="overflow-y-hidden">
    <div class="2xl:container 2xl:mx-auto">
      <div class="flex justify-between">
        <div class="mb-4 px-2 w-full">
          <label class="block mb-1 text-sm">Name:</label>

          <input v-model="category.name" class="w-full border px-4 py-2 rounded focus:border-blue-500 focus:shadow-outline outline-none" type="text" autofocus placeholder="Dairy Products" />
        </div>

        <div class="mb-4 px-2 w-full">
          <label class="block mb-1 text-sm">Tax Percentage:</label>

          <input v-model="category.tax" type="number" class="w-full border px-4 py-2 rounded focus:border-blue-500 focus:shadow-outline outline-none" min="0" max="100" step="5" />
        </div>
      </div>

      <div class="flex justify-between">
        <div class="mb-4 px-2 w-full">
          <label class="block mb-1 text-sm">Image:</label>

          <input v-model="category.image" class="w-full border px-4 py-2 rounded focus:border-blue-500 focus:shadow-outline outline-none" type="text" autofocus placeholder="Link to JPG | PNG image" />
        </div>
      </div>

      <div class="mb-4 px-2 w-full">
        <button v-on:click="submit" class="mx-2 px-4 py-2 text-sm rounded text-white bg-green-500 focus:outline-none hover:bg-green-400">Create</button>

        <nuxt-link to="/categories" class="mx-2 px-4 py-2 text-sm rounded text-white bg-blue-500 focus:outline-none hover:bg-blue-400">Back</nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      category: {
        name: "",
        tax: 0,
        image: "",
      },
    };
  },
  methods: {
    submit() {
      axios
        .post("http://127.0.0.1:8888/api/v1/categories", this.category, {
          headers: {
            "Content-Type": "application/x-www-form-urlencoded",
          },
        })
        .then((response) => {
          alert(`Category created successfully #${response.data.id}`);
        })
        .catch((error) => {
          const message = error.response.data.error;

          alert(message);
        });
    },
  },
};
</script>
