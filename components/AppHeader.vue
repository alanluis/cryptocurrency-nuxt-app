<template>
  <div>
    <nav class="bg-blue-500 p-4">
      <div class="container mx-auto flex justify-between items-center">
        <nuxt-link to="/" class="text-white font-bold text-xl">Home</nuxt-link>
        <div class="space-x-4">
          <nuxt-link to="/about" class="text-white">About</nuxt-link>
        </div>
      </div>
    </nav>
    <header class="bg-gray-800 text-white text-center py-8">
      <div class="container mx-auto">
        <h1 class="text-4xl font-bold mb-4">Cryptocurrency VueJs App</h1>
        <p class="text-lg">Explore Cryptocurrencies</p>
      </div>
    </header>
  </div>
</template>

<script>
export default {
  name: "AppHeader",
};
</script>
