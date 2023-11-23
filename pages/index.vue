<template>
  <div class="container mx-auto mt-8 p-4">
    <div v-if="!error">
      <SearchCoin v-on:search-coin="searchCoin"></SearchCoin>
      <CoinsTable :data="coins" />
      <div v-if="coins.length == 0" class="text-center mt-2">No markets were found matching your search criteria.</div>
    </div>
    <div v-if="error" class="text-center">An error has ocurred :(</div>
  </div>
</template>

<script>
import axios from "axios";
import CoinsTable from "../components/CoinsTable";
import CoinSearch from "../components/SearchCoin";

export default {
  components: {
    CoinsTable,
    CoinSearch,
  },

  data() {
    return {
      coins: [],
      error: false,
    };
  },

  async created() {
    try {
      const res = await axios.get(
        "http://localhost:8000/api/coins/markets?per_page=10",
        {
          headers: {
            Accept: "application/json",
          },
        }
      );

      this.coins = res.data;
    } catch (error) {
      console.log(error);
      this.error = true;
    }
  },

  methods: {
    async searchCoin(text) {
      try {
        const res = await axios.get(
          `http://localhost:8000/api/coins/markets?key=${text}`,
          {
            headers: {
              Accept: "application/json",
            },
          }
        );

        this.coins = res.data;
      } catch (error) {
        console.log(error);
        this.error = true;
      }
    },
  },
  
  head() {
    return {
      title: "Cryptocurrency App",
      meta: [
        {
          hid: "description",
          content: "Cryptocurrency App Vue.js Application",
        },
      ],
    };
  },
};
</script>
