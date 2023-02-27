<template>
  <div class="overflow-y-hidden">
    <div class="2xl:container 2xl:mx-auto">
      <div class="lg:px-20 md:px-6 px-4 md:py-12 py-8">
        <div class="flex justify-between items-center">
          <h1 class="text-3xl lg:text-4xl font-semibold text-gray-800 text-left">Orders</h1>

          <nuxt-link to="/orders/create">
            <SharedMoreButton></SharedMoreButton>
          </nuxt-link>
        </div>
      </div>
    </div>
  </div>
</template>
