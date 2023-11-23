<template>
  <div class="container mx-auto mt-8 p-4">
    <h1 class="text-3xl font-bold mb-4 text-center">About</h1>
    <h2 class="text-2sm font-bold mb-4 text-center">Cryptocurrency VueJs App</h2>
    <div class="text-center mb-4">Version 1.0.0</div>
    <div class="text-center">
        <button class="bg-blue-500 text-white py-2 px-4 rounded-full" @click="to()">Back to Home</button>
    </div>
  </div>
</template>

<script>
export default {
    methods: {
      to() {
        this.$router.push({ path: '/' })
      },
    },
    head() {
    return {
      title: "Crypto App - About",
      meta: [
        {
          hid: "description",
          content: "Cryptocurrency App Vue.js Application",
        },
      ],
    };
  },
}
</script>
