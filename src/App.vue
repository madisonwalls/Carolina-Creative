
<template>


  <div id="app">
    <!-- Form Component goes here -->
    <VideoPlayer></VideoPlayer>
    <Favorites></Favorites>
    <Filters></Filters>
    <Art></Art>
    <Card v-for="card in cards" :card="card"></Card>

  </div>
</template>

<script>
import axios from 'axios'
import Favorites from './components/Favorites'
import VideoPlayer from './components/VideoPlayer'
import Card from './components/Card'
import Filters from './components/Filters'
import Art from './components/Art'
export default {
  name: 'app',
  data () {
    return {
      cards: []
    }
  },
  mounted () {
    console.log('App -> mounted.')
    axios.get('/static/courses.json')
      .then((response) => {
        console.log(response.data)
        this.cards = response.data
      })
  },
  beforeDestroy () {
    console.log('App -> beforeDestroy.')
  },
  components: {
    Favorites,
    VideoPlayer,
    Card,
    Filters,
    Art
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
margin: 0px;
}

#app {

  margin: auto;
  display: block;

}

</style>
