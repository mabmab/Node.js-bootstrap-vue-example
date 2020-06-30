<!-- テンプレート -->
<template>
  <div class="weather-map">
    <b-card
        v-bind:title="city"
        img-src="https://placekitten.com/300/300/"
        img-alt="Image"
        img-top
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
import axios from 'axios'

export default {
  name: 'WeatherMap',
  data() {
    return {
        // Jsonのデータを格納
        weather: '???',
        temperature : '???',
        humidity: '???',
        pressure: '???'
    };
  },
  props: {
    city: String
  },
  methods: {
    async get_weather_map() {
        const abszero = -273.15; // 絶対零度
        var location = `${this.city},jp`;
        var APIKEY = process.env.OPENWEATHERMAP_APIKEY;
        console.log(`APIKEY: ${APIKEY}`);
        var URL = 'https://api.openweathermap.org/data/2.5/weather';

        const params = {
            q: location,
            APPID: APIKEY
        }

        await axios.get(URL, { params })
        // thenで成功した場合の処理をかける
        .then(response => {
            console.log(`status: ${response.status}`);
            console.log(`location: ${response.data.name}`);
            console.log(`date: ${new Date(response.data.dt*1000).toLocaleDateString('ja-jp')}`);
            console.log(`date: ${new Date(response.data.dt*1000).toLocaleTimeString('ja-jp')}`);
            console.log('-----');
            console.log('body:', response.data);
            this.weather = response.data.weather[0].main;
            this.temperature = `${(response.data.main.temp + abszero).toFixed(2)}(C)`;
            this.humidity = `${(response.data.main.humidity)}(%)`;
            this.pressure = `${(response.data.main.pressure)}(hp)`;
        }
        // catchでエラー時の挙動を定義する
        ).catch(err => {
            console.log('err:', err);
        });
    }
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
