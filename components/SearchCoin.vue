<template>
  <div class="bg-white p-8 w-200 text-center">
    <form @submit.prevent="onSubmit" action="#" method="GET">
      <div class="flex items-center">
        <input
          type="text"
          v-model="text"
          name="search"
          placeholder="Coin name or ID"
          class="flex-1 py-2 px-4 border border-gray-300 rounded-l focus:outline-none focus:ring focus:border-blue-500"
        />
        <button
          type="submit"
          class="bg-blue-500 text-white py-2 px-4 rounded-r"
        >
          Search
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "SearchCoin",

  data() {
    return {
      text: "",
    };
  },

  methods: {
    onSubmit() {
      this.$emit("search-coin", this.text);
      this.text = "";
    },
  },
};
</script>
