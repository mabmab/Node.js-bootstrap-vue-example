<!-- テンプレート -->
<template>
  <div class="weather-map">
    <h1>{{ city }}</h1>
    <b-card
        title="photo"
        img-src="https://placekitten.com/300/300/"
        img-alt="Image"
        img-top
        class="mb-2"
    />
  </div>
</template>

<!-- スクリプト -->
<script>
export default {
  name: 'WeatherMap',
  props: {
    city: String
  }
}
</script>

<!-- スタイル -->
<!-- Note: Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
