<template>
  <div class="border rounded-lg overflow-hidden dark:border-gray-700">
    <table class="min-w-full bg-white border border-gray-300 rounded-lg">
      <thead>
        <tr>
          <th class="py-2 px-4 border-b"></th>
          <th class="py-2 px-4 border-b">Name</th>
          <th class="py-2 px-4 border-b text-right">Current Price</th>
          <th class="py-2 px-4 border-b text-right">Total Volume</th>
          <th class="py-2 px-4 border-b text-right">Market Cap</th>
          <th class="py-2 px-4 border-b text-right">Market Cap Rank</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, itemIndex) in data" :key="itemIndex">
          <td class="py-2 px-4 border-b"><img :src="item.image" :alt="item.name" width="50"/></td>
          <td class="py-2 px-4 border-b">
            <nuxt-link :to="'coins/' + item.id"><a class="rounded-full bg-blue-500 text-white py-1 px-4">{{item.name}}</a></nuxt-link>
          </td>
          <td class="py-2 px-4 border-b text-right">{{ item.current_price.toLocaleString('en', { style: 'currency', currency: 'USD' }) }}</td>
          <td class="py-2 px-4 border-b text-right">{{ item.total_volume.toLocaleString('en', { style: 'currency', currency: 'USD' }) }}</td>
          <td class="py-2 px-4 border-b text-right">{{ item.market_cap.toLocaleString('en', { style: 'currency', currency: 'USD' }) }}</td>
          <td class="py-2 px-4 border-b text-right">#{{ item.market_cap_rank }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "CoinsTable",
  props: ["data"],
};
</script>

