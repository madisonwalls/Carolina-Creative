
<template>


  <div id="app">
    <!-- Form Component goes here -->
    <Favorites></Favorites>

  </div>
</template>

<script>
import Favorites from './components/Favorites'
export default {
  name: 'app',
  data () {
    return {
    }
  },
  mounted () {
    console.log('App -> mounted.')
  },
  beforeDestroy () {
    console.log('App -> beforeDestroy.')
  },
  components: {
    Favorites
  },
  methods: {

  }
}
</script>

<style>

@font-face {
font-family: carolinaCreative;
src: url(../fonts/white_festive_demo.otf);
}

.title h1 {
font-family: carolinaCreative;
font-size: 70px;
padding: 30px;
color: #7F1637;
text-decoration: underline;
}

</style>
