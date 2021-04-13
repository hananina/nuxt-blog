<template>
  <div>
    <!-- <p>time:{{ data.time.updated }}</p>
    <p>chartName:{{ data.chartName }}</p>
    <p>USD:{{ data.bpi.USD.rate }}</p> -->
    <p>weather:{{ data }}</p>
  </div>
</template>

<script>
export default {
  // async asyncData({ $axios }) {
  //   const ip = await $axios.$get('http://icanhazip.com')
  //   return { ip }
  // }

  async asyncData({ $axios }) {
    const response = await $axios.$get(
      "https://api.openweathermap.org/data/2.5/weather?id=2172797&appid=be56ce65affba360fcfb08d130f572b1"
    );
    return { data: response };
  }

  // async asyncData({ $axios }) {
  //   const response = await $axios.$get(
  //     "https://api.coindesk.com/v1/bpi/currentprice.json"
  //   );
  //   return {
  //     data: response
  //   };
  // }
};
</script>
