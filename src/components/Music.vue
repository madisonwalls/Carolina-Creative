<!--Shows Music Sub Category Cards -->
<template>
<div class="Music">
    <div class="cardPosition">
  <div v-for="musicCard in musicCards" :class="{ 'musicCard': true, 'active': activeButton === musicCard }"  @click="clickCategory(musicCard)">
    <p>{{ musicCard.musicTitle }}</p>
    <img v-bind:src="musicCard.image">
  </div>
</div>
  <Card v-for="card in cards" :card="card" class="boxing" @addFavorite="onAddFavorite"></Card>
  <div  v-show="activeButton === null">
    <img src="/static/img/ccimage.png">
      <h1>Pick a Sub Category to View Options</h1>
  </div>

</div>
</template>

<script>
import axios from 'axios'
import Card from './Card'
export default {
  mounted () {
    console.log('Music -> mounted.')
    console.log(this.musicCards)
    axios.get('/static/courses.json')
      .then((response) => {
        console.log(response.data)
        this.cards = response.data
      })
  },
  beforeDestroy () {
    console.log('Music -> beforeDestroy.')
  },
  props: [

  ],
  data () {
    return {
      activeButton: null,
      musicCards:
      [
        {
          musicTitle: 'Composition',
          image: '/static/img/composition.jpg'
        },
        {
          musicTitle: 'Instrumental Performance',
          image: '/static/img/violin.jpg'
        },
        {
          musicTitle: 'Music Theory',
          image: '/static/img/musictheory.jpg'
        },
        {
          musicTitle: 'Piano Performance',
          image: '/static/img/piano.jpg'
        },
        {
          musicTitle: 'Voice Performance',
          image: '/static/img/voice.jpg'
        },
        {
          musicTitle: 'Popular Music',
          image: '/static/img/popularmusic.jpg'
        }
      ],
      cards: []
    }
  },
  methods: {
      // <!-- Tells the Filter Component which category to show -->
    clickCategory (musicCard) {
      this.activeButton = musicCard
      this.$evt.$emit('clickCategory', {
        categoryTitle: this.activeButton.musicTitle
      })
    },
    // <!-- Puts the card in the Favorites Box-->
    onAddFavorite (data) {
      this.$emit('addFavorite', data)
    }
  },
  components: {
    Card
  }
}
</script>

<style scoped>

.Music {
  margin: auto;
  display: block;
  width: 1200px;
}

.musicCard {

  border: 5px solid #7F1637;
  display: inline-block;
  margin: 20px;
  font-family: avenir;
  font-size: 28px;
  text-align: center;
  width: 250px;
  height: 250px;

}

.musicCard:hover  {

background-color: #7F1637;
cursor: pointer;
}

.active {
  background-color: #7F1637;
}

.active p {
  color: white;
  z-index: 0;
}

.musicCard img {
  width: 250px;
  height: 250px;
  position: relative;
  opacity: .4;
}


h1 {
  font-family: carolinaCreative;
  font-size: 45px;
  text-align: center;
  color: #7F1637;
  padding: 15px;
  padding-bottom: 0px;
  position: relative;
}

p {
  font-family: avenir;
  font-weight: bold;
  font-size: 28px;
  color: #7F1637;
  padding-top: 100px;
  z-index: 5;
  margin: auto 50px;
  display: block;
  text-align: center;
  position: absolute;
  text-align: center;
  width: 100px;
}

.boxing {
  background-color: white;
  padding: 15px;
  border: 1px solid #ccc;
  margin: 10px;
}

img {
  width: 50%;
  height: auto;
  display: block;
  margin: auto;
  opacity: 0.3;
  position: relative;
  float: right;

}
@media screen and (max-width: 460px){


    .Music {
      margin: auto;
      display: block;
      width: 350px;
    }

    .musicCard {

      border: 3px solid #7F1637;
      display: inline-block;
      margin: 5px;
      font-family: avenir;
      font-size: 28px;
      text-align: center;
      width: 150px;
      height: 150px;

    }

    .musicCard img {
      width: 150px;
      height: 150px;
      position: relative;
      opacity: .4;
    }

    p {
      font-family: avenir;
      font-weight: bold;
      font-size: 20px;
      color: #7F1637;
      padding-top: 50px;
      z-index: 5;
      margin: auto 0px;
      display: block;
      text-align: center;
      position: absolute;
      padding-left: 0px;
    }

    img {
      opacity: 0;
    }

    h1 {
      display: none;
    }

  }




</style>
