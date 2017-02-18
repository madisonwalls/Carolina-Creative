<!-- App that writes all the components out -->
<template>
  <div id="app">
    <!--Components-->
    <VideoPlayer></VideoPlayer>
    <Favorites :favorites="favorites"></Favorites>
    <Filters></Filters>
    <transition name="fade">
    <Art v-show="newTab === 'Art'" @addFavorite="onAddFavorite"></Art>
    </transition>
    <transition name="fade">
    <Music v-show="newTab === 'Music'" @addFavorite="onAddFavorite"></Music>
    </transition>
    <transition name="fade">
    <Writing v-show="newTab === 'Writing'" @addFavorite="onAddFavorite"></Writing>
    </transition>
    <transition name="fade">
    <Theatre v-show="newTab === 'Theatre'" @addFavorite="onAddFavorite"></Theatre>
    </transition>
    <transition name="fade">
    <Clubs v-show="newTab === 'Clubs'" @addFavorite="onAddFavorite"></Clubs>
    </transition>
    <transition name="fade">
    <All v-show="newTab === 'All'" @addFavorite="onAddFavorite"></All>
    </transition>
    <bottomFooter></bottomFooter>
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
    // <!-- Takes information from filter component and updates the category component shown -->
    changeFilter (data) {
      console.log('App -> changeFilter', data)
      this.newTab = data.newTab
      console.log(this.newTab)
    },
    // <!-- Adds Favorite from card component-->
    onAddFavorite (data) {
      this.name = data.name
      console.log(this.name)
      this.favoriteid++
      this.favorites.push({
        name: this.name,
        id: this.favoriteid
      })
      console.log('favorites', this.favorites)
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
  height: 2000px;
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



.fade-enter-active {
  transition: opacity 1s;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
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
