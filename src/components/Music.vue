<template>
<div class="Music">
  <div v-for="musicCard in musicCards" :class="{ 'musicCard': true, 'active': activeButton === musicCard }"  @click="clickCategory(musicCard)">
    <p>{{ musicCard.musicTitle }}</p>
    <img v-bind:src="musicCard.image">
  </div>
  <Card v-for="card in cards" :card="card" class="boxing" @addFavorite="onAddFavorite" @removeFavorite="onRemoveFavorite"></Card>


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
    clickCategory (musicCard) {
      this.activeButton = musicCard
      this.$evt.$emit('clickCategory', {
        categoryTitle: this.activeButton.musicTitle
      })
    },
    onAddFavorite (data) {
      this.$emit('addFavorite', data)
    },
    onRemoveFavorite () {
      console.log('hey')
      this.$emit('removeFavorite')
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
  width: 1000px;
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
  text-decoration: underline;
  color: #7F1637;
  padding: 15px;
  padding-bottom: 0px;
}

p {
  font-family: avenir;
  font-size: 24px;
  color: #7F1637;
  padding-top: 80px;
  position: absolute;
  z-index: 5;
  padding-left: 60px;
  text-align: center;
  width: 100px;
}

.boxing {
  background-color: white;
  padding: 15px;
  border: 1px solid #ccc;
  margin: 10px;
}



</style>
