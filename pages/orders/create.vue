<template>
  <div class="flex flex-col items-center border-b bg-white py-4 sm:flex-row sm:px-10 lg:px-20 xl:px-32">
    <a href="#" class="text-2xl font-bold text-gray-800">Order #123</a>
    <OrderProgress></OrderProgress>
  </div>
  <div class="grid sm:px-10 lg:grid-cols-2 lg:px-20 xl:px-32">
    <div class="px-4 pt-8">
      <p class="text-xl font-medium">Order Summary</p>
      <p class="text-gray-400">Check your items. And select a suitable shipping method.</p>
      <div class="mt-8 space-y-3 rounded-lg border bg-white px-2 py-4 sm:px-6">
        <div v-for="item in items" v-bind:key="item.key" class="flex flex-col rounded-lg bg-white sm:flex-row">
          <img class="m-2 h-24 w-28 rounded-md border object-cover object-center" :src="item.image" alt="" />
          <div class="flex w-full flex-col px-4 py-4">
            <span class="font-semibold">{{ item.name }}</span>
            <p class="mt-auto font-semibold">Quantity: {{ item.quantity }}</p>
            <p class="mt-auto text-lg font-bold">${{ item.price / 100 }}</p>
          </div>
        </div>

        <div class="flex flex-col rounded-lg bg-white sm:flex-row">
          <img class="m-2 h-24 w-28 rounded-md border object-cover object-center" :src="settings.display.image" alt="" />
          <div class="flex w-full flex-col px-4 py-4">
            <div class="relative inline-block w-full text-gray-700">
              <select class="w-full h-10 pl-3 pr-6 text-base placeholder-gray-600 border rounded-lg appearance-none focus:shadow-outline" @change="handleNameChange" placeholder="Regular input">
                <option v-for="product in settings.products" v-bind:key="product.key" :value="product.id">{{ product.name }}</option>
              </select>
              <div class="absolute inset-y-0 right-0 flex items-center px-2 pointer-events-none">
                <svg class="w-4 h-4 fill-current" viewBox="0 0 20 20">
                  <path d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd" fill-rule="evenodd"></path>
                </svg>
              </div>
            </div>

            <div class="flex flex-row justify-between mt-2">
              <div>
                <p class="mt-auto text-lg font-bold">${{ settings.display.price / 100 }}</p>
              </div>
              <div>
                <span class="font-semibold">Quantity: <input class="border-solid border-gray-300" @change="handleQuantityChange" type="number" min="1" max="10" step="1" :value="settings.form.quantity" /></span>
              </div>
              <div>
                <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 border border-blue-700 rounded" v-on:click="addProduct">Add to Cart</button>
              </div>
            </div>
          </div>
        </div>
      </div>

      <p class="mt-8 text-lg font-medium">Shipping Methods</p>
      <OrderShippingMethod></OrderShippingMethod>
    </div>
    <OrderPaymentDetail :items="items"></OrderPaymentDetail>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      items: [],
      settings: {
        form: {
          product_id: 0,
          quantity: 1,
        },
        display: {
          price: 0,
          image: "",
        },
        logo: {
          fedex: "",
        },
        products: [],
      },
    };
  },
  mounted() {
    const categoryRequest = axios.get("http://127.0.0.1:8888/api/v1/categories", this.product);

    categoryRequest.then((categoryResponse) => {
      this.settings.categories = categoryResponse.data;

      const productRequest = axios.get("http://127.0.0.1:8888/api/v1/products", this.product);
      productRequest.then((productResponse) => {
        this.settings.products = productResponse.data.map((product) => {
          product.category = this.findCategoryById(product.category_id);

          return product;
        });

        const first = this.settings.products.find((n) => n);

        this.settings.display.price = first.price;
        this.settings.display.image = first.image;
      });
    });
  },
  methods: {
    handleQuantityChange($e) {
      this.settings.form.quantity = $e.target.value;

      this.updatePrice();
    },
    handleNameChange($e) {
      this.settings.form.product_id = $e.target.value;

      this.updatePrice();
    },
    updatePrice() {
      const { quantity, product_id } = this.settings.form;

      const product = this.findProductById(product_id);

      this.settings.display.price = product.price * quantity;
    },
    addProduct() {
      const { quantity, product_id } = this.settings.form;

      const product = this.findProductById(product_id);

      this.items.push({
        quantity,
        ...product,
      });
    },
    findProductById(id) {
      return this.settings.products.find((product) => product.id === parseInt(id)) || this.settings.products.find((n) => n);
    },
    findCategoryById(id) {
      return this.settings.categories.find((category) => category.id === id);
    },
  },
};
</script>
