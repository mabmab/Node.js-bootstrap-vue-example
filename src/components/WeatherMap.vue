<!-- テンプレート -->
<template>
  <div class="weather-map">
    <b-card
      :img-src="getImgUrl(icon)"
      v-bind:img-alt="icon"
      img-top
      v-bind:title="city"
      class="mb-2"
    >
      <p>Weather: {{weather}}</p>
      <p>Temperature: {{temperature}}</p>
      <p>Humidity: {{humidity}}</p>
      <p>Pressure: {{pressure}}</p>
    </b-card>
  </div>
</template>

<!-- スクリプト -->
<script>
import axios from 'axios';
var icon_sunny = 'f_f_traffic_7_s512_f_traffic_7_0bg';
var icon_clouds = 'f_f_traffic_4_s512_f_traffic_4_0bg';
var icon_rain = 'f_f_traffic_5_s512_f_traffic_5_0bg';

export default {
  name: 'WeatherMap',
  data() {
    return {
        // Jsonのデータを格納
        weather: '???',
        temperature : '???',
        humidity: '???',
        pressure: '???',
        icon: icon_sunny
    };
  },
  props: {
    city: String
  },
  methods: {
    async get_weather_map() {
        const abszero = -273.15; // 絶対零度
        var URL = 'https://api.openweathermap.org/data/2.5/weather';
        const params = {
            q: `${this.city},jp`,
            APPID: process.env.VUE_APP_OPENWEATHERMAP_APIKEY
        }
        await axios.get(URL, { params })
        // thenで成功した場合の処理をかける
        .then(response => {
            console.log(`status: ${response.status}`);
            console.log(`location: ${response.data.name}`);
            console.log(`date: ${new Date(response.data.dt*1000).toLocaleDateString('ja-jp')}`);
            console.log(`time: ${new Date(response.data.dt*1000).toLocaleTimeString('ja-jp')}`);
            console.log('-----');
            console.log('body:', response.data);
            this.weather = response.data.weather[0].main;
            if (this.weather === 'Rain') this.icon = icon_rain;
            else if (this.weather === 'Clouds') this.icon = icon_clouds;
            else this.icon = icon_sunny;
            this.temperature = `${(response.data.main.temp + abszero).toFixed(2)}(C)`;
            this.humidity = `${(response.data.main.humidity)}(%)`;
            this.pressure = `${(response.data.main.pressure)}(hp)`;
        }
        // catchでエラー時の挙動を定義する
        ).catch(err => {
            console.log('err:', err);
        });
    },
    getImgUrl(name) {
      var images = require.context('../assets/', false, /f_f_traffic.+\.png$/);
      return images('./' + name + ".png");
    },
  },
  async created() {
    await this.get_weather_map();
  }
}
</script>

<!-- スタイル -->
<!-- Note: Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
p {
  font-size: 1.3em;
}
</style>
