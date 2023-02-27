<template>
  <div class="bg-gray-50 p-8 transform transition duration-500 hover:scale-110 border-2 rounded-md hover:border-gray-500">
    <h2 class="text-xl text-gray-800 font-semibold">{{ name }}</h2>
    <h2>
      <slot></slot>
    </h2>
    <div class="flex justify-center items-center mt-4 md:mt-19">
      <img class="w-full h-52" :src="image" :alt="name" role="img" />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true,
    },
    image: {
      type: String,
      required: true,
    },
  },
};
</script>
