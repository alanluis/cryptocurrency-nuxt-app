<template>
  <div class="container mx-auto mt-2 p-4">
      <h1 class="text-3xl font-bold mb-4 text-center">Coin details for {{ data.name }} ({{ data.symbol?.toUpperCase() }})</h1>
      <div class="container mx-auto text-center mb-2">
          <img :src="data?.image?.large" :alt="data.name" class="mx-auto mb-4">
      </div>

      <div class="border rounded-lg overflow-hidden dark:border-gray-700">
        <table class="min-w-full bg-white border border-gray-300">
          <thead class="bg-gray-200">
            <tr>
              <th class="py-2 px-4 border-b">Property</th>
              <th class="py-2 px-4 border-b">Value</th>
            </tr>
          </thead>
          <tbody>
            <tr><td class="py-2 px-4 border-b">Name</td><td class="py-2 px-4 border-b">{{ data.name }}</td></tr>
            <tr><td class="py-2 px-4 border-b">Market Cap Rank</td><td class="py-2 px-4 border-b">#{{ data.market_cap_rank }}</td></tr>
            <tr><td class="py-2 px-4 border-b">Current Price</td><td class="py-2 px-4 border-b">{{ toCurrencyFormat(data.market_data?.current_price?.usd) }}</td></tr>
            <tr><td class="py-2 px-4 border-b">Market Cap</td><td class="py-2 px-4 border-b">{{ toCurrencyFormat(data.market_data?.market_cap?.usd) }}</td></tr>
            <tr><td class="py-2 px-4 border-b">Total Volume</td><td class="py-2 px-4 border-b">{{ toCurrencyFormat(data.market_data?.total_volume?.usd) }}</td></tr>
            <tr><td class="py-2 px-4 border-b">Last updated</td><td class="py-2 px-4 border-b">{{ data.market_data?.last_updated }}</td></tr>
          </tbody>
        </table>
      </div>
    </div>
</template>

<script>
import numeral from 'numeral';

export default {
  name: "CoinInfo",
  props: ["data"],
  methods: {
    toCurrencyFormat(data) {
      return numeral(data).format('$0,0.00');
    },
  }
}
</script>
