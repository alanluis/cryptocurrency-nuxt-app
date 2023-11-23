<template>
  <div>
    <div v-if="error" class="text-center m-4">
      An error has ocurred :(
    </div>
    <div class="text-center">
        <button class="bg-blue-500 text-white py-2 px-4 m-4 rounded-full" @click="to()">Back to List</button>
    </div>
    <div v-if="!error">
      <CoinInfo :data="coin"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import CoinInfo from '../../../components/CoinInfo'

export default {
  components: {
    CoinInfo,
  },

  data() {
    return {
      coin: {},
      error: false,
    }
  },

  async created() {
    const config = {
      headers: {
        Accept: "application/json",
      },
    };

    try {
      const res = await axios.get(
        "http://localhost:8000/api/coins/" + this.$route.params.id,
        config
      );

      this.coin = res.data;
    } catch (error) {
      console.log(error);
      this.error = true;
    }
  },

  methods: {
      to() {
        this.$router.push({ path: '/' })
      },
  },

  head() {
    return {
      title: "Cryptocurrency App - " + this.coin?.name,
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
