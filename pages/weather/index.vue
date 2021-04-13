<template>
  <div>
    <ul>
      <li>場所の名前: {{ data.name }}</li>
      <li>Lon:{{ data.coord.lon }} Lat:{{ data.coord.lat }}</li>
      <li>天気:{{ data.weather[0].description }}</li>
      <li>温度:{{ data.main.temp }}</li>
      <li></li>
    </ul>
  </div>
</template>

<script>
export default {
  // async asyncData({ $axios }) {
  //   const response = await $axios.$get(
  //     "https://api.openweathermap.org/data/2.5/weather?id=2172797&appid=5f2899a04c5660712577c79c9ef9205b"
  //   );
  //   return { data: response };
  // }
  async asyncData({ $axios }) {
    const response = await $axios.$get(
      "https://api.openweathermap.org/data/2.5/weather",
      {
        params: {
          q: "boston",
          appid: "5f2899a04c5660712577c79c9ef9205b",
          lang: "ja"
        }
      }
    );
    return { data: response };
  }
};
</script>
