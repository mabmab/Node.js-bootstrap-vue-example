<!-- テンプレート -->
<template>
  <div id="app">
    <!-- ヘッダー -->
    <header>
      <b-collapse class="bg-dark" id="navbarHeader">
        <div class="container">
          <div class="row">
            <div class="col-sm-8 col-md-7 py-4">
              <h4 class="text-white">About</h4>
              <p class="text-muted">This website was created using Vue, Bootstrap, and Bootstrap Vue. Please note that it is a site created for programming learning and has no function.</p>
            </div>
            <div class="col-sm-4 offset-md-1 py-4">
              <h4 class="text-white">Contact</h4>
              <ul class="list-unstyled">
                <li><a href="#" class="text-white">Follow on Twitter</a></li>
                <li><a href="#" class="text-white">Like on Facebook</a></li>
                <li><a href="#" class="text-white">Email me</a></li>
              </ul>
            </div>
          </div>
        </div>
      </b-collapse>
      <div class="navbar navbar-dark bg-dark box-shadow">
        <div class="container d-flex justify-content-between">
          <a href="#" class="navbar-brand d-flex align-items-center">
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mr-2">
              <path d="M23 19a2 2 0 0 1-2 2H3a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h4l2-3h6l2 3h4a2 2 0 0 1 2 2z"></path>
              <circle cx="12" cy="13" r="4"></circle>
            </svg>
            <strong>BootstrapVue</strong>
          </a>
          <b-button v-b-toggle.navbarHeader variant="outline-secondary">
            <span class="navbar-toggler-icon"></span>
          </b-button>
        </div>
      </div>
    </header>
    <!-- メイン -->
    <main role="main">
      <b-jumbotron header="BootstrapVue" lead="Bootstrap v4 Components for Vue.js 2">
          <img alt="Vue logo" src="./assets/logo.png">
          <HelloWorld msg="Welcome to BootstrapVue App"/>
      </b-jumbotron>
      <div class="container">
        <div class="row">
          <div class="col-md-4">
            <WeatherMap city="Tokyo"/>
          </div>
          <div class="col-md-4">
            <WeatherMap city="Osaka"/>
          </div>
          <div class="col-md-4">
            <WeatherMap city="Nagoya"/>
          </div>
          <div class="col-md-4">
            <WeatherMap city="Fukuoka"/>
          </div>
          <div class="col-md-4">
            <WeatherMap city="Sapporo"/>
          </div>
          <div class="col-md-4">
            <WeatherMap city="Hamamatsu"/>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<!-- スクリプト -->
<script>
import HelloWorld from './components/HelloWorld.vue'
import WeatherMap from './components/WeatherMap.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    WeatherMap
  }
}
</script>

<!-- スタイル -->
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
