<template>
  <div id="app">
    <v-home></v-home>
    <v-news></v-news>
  </div>
</template>

<script>
import Home from './components/Home.vue'
import News from './components/News.vue'
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  components:{
  	'v-home':Home,
  	'v-news':News
  }
}
</script>

<style lang="scss">

</style>
