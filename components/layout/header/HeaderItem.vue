<template>
  <nuxt-link :to="link" class="block py-2 pl-3 pr-4 text-gray-700 rounded hover:bg-gray-100 md:hover:bg-transparent md:hover:text-blue-700 md:p-0 dark:text-gray-400 md:dark:hover:text-blue-500 dark:hover:bg-gray-700 dark:hover:text-blue-500 md:dark:hover:bg-transparent dark:border-gray-700">
    <slot></slot>
  </nuxt-link>
</template>

<script>
export default {
  props: {
    link: {
      type: String,
      required: true,
    },
  },
};
</script>
