
<template>


  <div id="app">
    <!-- Form Component goes here -->
    <VideoPlayer></VideoPlayer>
    <Favorites :favorites="favorites"></Favorites>
    <Filters></Filters>
    <Art v-show="newTab === 'Art'" @addFavorite="onAddFavorite"  @removeFavorite="onRemoveFavorite"></Art>
    <Music v-show="newTab === 'Music'" @addFavorite="onAddFavorite" @removeFavorite="onRemoveFavorite"></Music>
    <Writing v-show="newTab === 'Writing'" @addFavorite="onAddFavorite" @removeFavorite="onRemoveFavorite"></Writing>
    <Theatre v-show="newTab === 'Theatre'" @addFavorite="onAddFavorite" @removeFavorite="onRemoveFavorite"></Theatre>
    <Clubs v-show="newTab === 'Clubs'" @addFavorite="onAddFavorite" @removeFavorite="onRemoveFavorite"></Clubs>
    <All v-show="newTab === 'All'" @addFavorite="onAddFavorite" @removeFavorite="onRemoveFavorite"></All>
    <Footer></Footer>


  </div>
</template>

<script>
import axios from 'axios'
import Favorites from './components/Favorites'
import VideoPlayer from './components/VideoPlayer'
import Card from './components/Card'
import Filters from './components/Filters'
import Art from './components/Art'
import Music from './components/Music'
import Writing from './components/Writing'
import Theatre from './components/Theatre'
import Clubs from './components/Clubs'
import All from './components/All'
import Footer from './components/Footer'
export default {
  name: 'app',
  data () {
    return {
      name: '',
      favoriteid: '',
      newTab: '',
      favorites: []
    }
  },
  mounted () {
    console.log('App -> mounted.')
    this.$evt.$on('clickButton', this.changeFilter)
    this.$evt.$on('removeFavorite', this.onRemoveFavorite)
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
    Art,
    Music,
    Writing,
    Theatre,
    Clubs,
    All,
    Footer
  },
  methods: {
    changeFilter (data) {
      console.log('App -> changeFilter', data)
      this.newTab = data.newTab
      console.log(this.newTab)
    },
    onAddFavorite (data) {
      this.name = data.name
      console.log(this.name)
      this.favoriteid++
      this.favorites.push({
        name: this.name,
        id: this.favoriteid
      })
      console.log('favorites', this.favorites)
    },
    onRemoveFavorite (i) {
      this.favorites.splice(i, 1)
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
