<template>
  <div class="overflow-y-hidden">
    <div class="2xl:container 2xl:mx-auto">
      <div class="flex justify-between items-center">
        <h1 class="text-3xl lg:text-4xl font-semibold text-gray-800 text-left">Orders</h1>
        <nuxt-link to="/orders/create">
          <SharedMoreButton></SharedMoreButton>
        </nuxt-link>
      </div>
      <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
        <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
          <tr>
            <th scope="col" class="px-6 py-3">Id</th>
            <th scope="col" class="px-6 py-3">Created At</th>
            <th scope="col" class="px-6 py-3">Products</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="{ id, created_at, order_products } in orders" class="bg-white border-b dark:bg-gray-900 dark:border-gray-700">
            <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">{{ id }}</th>
            <td class="px-6 py-4">{{ created_at }}</td>
            <td class="px-6 py-4">
              <span v-for="orderProduct in order_products" class="mx-2">#{{ orderProduct.product_id }}</span>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      orders: [],
    };
  },
  async created() {
    const { data } = await axios.get(`${this.$config.APP_URL}/v1/orders`);

    this.orders = data;
  },
};
</script>
