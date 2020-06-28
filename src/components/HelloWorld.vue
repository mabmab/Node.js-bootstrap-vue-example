<!-- テンプレート -->
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <b-button variant="primary" @click="clickButton">Button</b-button>
  </div>
</template>

<!-- スクリプト -->
<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods: {
    clickButton() {
      alert('Button pressed')
    }
  }
}
</script>

<!-- スタイル -->
<!-- Note: Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
