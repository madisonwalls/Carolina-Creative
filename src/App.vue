
<template>


  <div id="app">
    <!-- Form Component goes here -->
    <VideoPlayer></VideoPlayer>
    <Favorites :favorites="favorites"></Favorites>
    <Filters></Filters>
    <Art v-show="newTab === 'Art'" @addFavorite="onAddFavorite" @removeFavorite="onRemoveFavorites"></Art>


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
      newTab: '',
      favorites: []
    }
  },
  mounted () {
    console.log('App -> mounted.')
    this.$evt.$on('clickButton', this.changeFilter)
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
    changeFilter (data) {
      console.log('App -> changeFilter', data)
      this.newTab = data.newTab
      console.log(this.newTab)
    },
    onAddFavorite (data) {
      this.favorites.push(data)
      console.log(data.name)
    }
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
