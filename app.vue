<template>
  <div class="flex flex-col h-screen">
    <header class="w-full text-center border-b border-grey p-4">
      <LayoutHeader></LayoutHeader>
    </header>

    <main class="flex-1 overflow-y-auto py-4">
      <NuxtPage />
    </main>

    <LayoutFooter></LayoutFooter>
  </div>
</template>
