<template>
<div class="All">
  <div v-for="allCard in allCards" :class="{ 'allCard': true, 'active': activeButton === allCard }"  @click="clickCategory(allCard)">
    <p>{{ allCard.allTitle }}</p>
    <img v-bind:src="allCard.image">
  </div>
  <Card v-for="card in cards" :card="card" class="boxing" @addFavorite="onAddFavorite" @removeFavorite="onRemoveFavorite"></Card>


</div>
</template>

<script>
import axios from 'axios'
import Card from './Card'
export default {
  mounted () {
    console.log('All -> mounted.')
    console.log(this.allCards)
    axios.get('/static/courses.json')
      .then((response) => {
        console.log(response.data)
        this.cards = response.data
      })
  },
  beforeDestroy () {
    console.log('All -> beforeDestroy.')
  },
  props: [

  ],
  data () {
    return {
      activeButton: null,
      allCards:
      [
        {
          allTitle: 'Painting',
          image: '/static/img/painting.jpg'
        },
        {
          allTitle: 'Sculpture',
          image: '/static/img/sculpture.jpg'
        },
        {
          allTitle: 'Drawing',
          image: '/static/img/drawing.jpg'
        },
        {
          allTitle: 'Photography',
          image: '/static/img/photography.jpg'
        },
        {
          allTitle: 'Digital Media',
          image: '/static/img/digitalmedia.jpg'
        },
        {
          allTitle: 'Mixed Media',
          image: '/static/img/mixedmedia.jpg'
        },
        {
          allTitle: 'Composition',
          image: '/static/img/composition.jpg'
        },
        {
          allTitle: 'Instrumental Performance',
          image: '/static/img/violin.jpg'
        },
        {
          allTitle: 'Music Theory',
          image: '/static/img/musictheory.jpg'
        },
        {
          allTitle: 'Piano Performance',
          image: '/static/img/piano.jpg'
        },
        {
          allTitle: 'Voice Performance',
          image: '/static/img/voice.jpg'
        },
        {
          allTitle: 'Popular Music',
          image: '/static/img/popularmusic.jpg'
        },
        {
          allTitle: 'Fiction',
          image: '/static/img/fiction.jpg'
        },
        {
          allTitle: 'Poetry',
          image: '/static/img/poetry.png'
        },
        {
          allTitle: 'Other',
          image: '/static/img/other.jpeg'
        },
        {
          allTitle: 'Acting',
          image: '/static/img/acting.jpg'
        },
        {
          allTitle: 'Drama',
          image: '/static/img/drama.JPG'
        },
        {
          allTitle: 'Theatre',
          image: '/static/img/theatre.jpg'
        },
        {
          allTitle: 'Play Writing',
          image: '/static/img/playwriting.jpeg'
        },
        {
          allTitle: 'Dance',
          image: '/static/img/dance.jpeg'
        },
        {
          allTitle: 'Comedy',
          image: '/static/img/comedy.jpeg'
        },
        {
          allTitle: 'Singing',
          image: '/static/img/singing.jpg'
        },
        {
          allTitle: 'Music',
          image: '/static/img/music.jpeg'
        },
        {
          allTitle: 'Club Theatre',
          image: '/static/img/theatreclub.jpg'
        },
        {
          allTitle: 'Club Poetry',
          image: '/static/img/poetryclub.jpg'
        }
      ],
      cards: []
    }
  },
  methods: {
    clickCategory (allCard) {
      this.activeButton = allCard
      this.$evt.$emit('clickCategory', {
        categoryTitle: this.activeButton.allTitle
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

.All {
  margin: auto;
  display: block;
  width: 1000px;
}

.allCard {

  border: 5px solid #7F1637;
  display: inline-block;
  margin: 20px;
  font-family: avenir;
  font-size: 28px;
  text-align: center;
  width: 250px;
  height: 250px;

}

.allCard:hover  {

background-color: #7F1637;
cursor: pointer;
}

.active {
  background-color: #7F1637;
}

.active p {
  color: white;
}

.allCard img {
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
