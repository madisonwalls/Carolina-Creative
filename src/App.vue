
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
    <!-- <bottomFooter></bottomFooter> -->


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
import bottomFooter from './components/bottomFooter'
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
    bottomFooter
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
padding-bottom: 0px;
color: #7F1637;
text-decoration: underline;
margin: 0px;
display: inline-block;
}

#app {

  margin: auto;
  display: block;

}

.cardPosition {
  display: inline-block;
  float: left;
  width: 50%;
  height: 1800px;
}

.boxing {
  background-color: white;
  padding: 15px;
  border: 1px solid #ccc;
  margin: 10px;
  border-radius: 10px;
}

.title p {
  font-family: avenir;
  font-size: 20px;
  color: #7F1637;
  margin-top: 0px;
  padding-left: 30px;
}



@media screen and (max-width: 460px) {

    .title h1 {
    font-family: carolinaCreative;
    font-size: 50px;
    padding: 20px;
    text-align: center;
    }

    .title p {
      font-size: 15px;
      text-align: center;
      padding: 0px;
    }

    .cardPosition {
      display: inline-block;
      float: left;
      width: 100%;
      height: auto;
    }

    [v-cloak] {
      display: none;
    }

}

</style>
