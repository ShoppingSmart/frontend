<template>
  <nav class="bg-white border-gray-200 dark:border-gray-600 dark:bg-gray-900">
    <div class="flex flex-wrap justify-between items-center mx-auto max-w-screen-xl px-4 md:px-6 py-2.5">
      <a href="https://www.softexpert.com" class="flex items-center">
        <img :src="logo" class="h-6 mr-3 sm:h-9" alt="Soft Expert Logo" />
        <span class="self-center text-xl font-semibold whitespace-nowrap dark:text-white">Soft Expert Testing App</span>
      </a>
      <div class="items-center justify-between hidden w-full md:flex md:w-auto md:order-1">
        <ul class="flex flex-col p-4 mt-4 border border-gray-100 rounded-lg bg-gray-50 md:flex-row md:space-x-8 md:mt-0 md:text-sm md:font-medium md:border-0 md:bg-white dark:bg-gray-800 md:dark:bg-gray-900 dark:border-gray-700">
          <li>
            <LayoutHeaderItem link="/">Home</LayoutHeaderItem>
          </li>
          <li>
            <LayoutHeaderItem link="/products">Products</LayoutHeaderItem>
          </li>
          <li>
            <LayoutHeaderItem link="/categories">Categories</LayoutHeaderItem>
          </li>
          <li>
            <LayoutHeaderItem link="/orders">Orders</LayoutHeaderItem>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      logo: "https://obr.global/wp-content/uploads/2018/05/Logo-SoftExpert.gif",
    };
  },
};
</script>
