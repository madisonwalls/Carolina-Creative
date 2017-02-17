<template>
<div class="Art">
  <div v-for="artCard in artCards" :class="{ 'artCard': true, 'active': activeButton === artCard }"  @click="clickCategory(artCard)">
    <p>{{ artCard.artTitle }}</p>
    <img v-bind:src="artCard.image">
  </div>
  <Card v-for="card in cards" :card="card" class="boxing" @addFavorite="onAddFavorite" @removeFavorite="onRemoveFavorite"></Card>


</div>
</template>

<script>
import axios from 'axios'
import Card from './Card'
export default {
  mounted () {
    console.log('Art -> mounted.')
    console.log(this.artCards)
    axios.get('/static/courses.json')
      .then((response) => {
        console.log(response.data)
        this.cards = response.data
      })
  },
  beforeDestroy () {
    console.log('Art -> beforeDestroy.')
  },
  props: [

  ],
  data () {
    return {
      activeButton: null,
      artCards:
      [
        {
          artTitle: 'Painting',
          image: '/static/img/painting.jpg'
        },
        {
          artTitle: 'Sculpture',
          image: '/static/img/sculpture.jpg'
        },
        {
          artTitle: 'Drawing',
          image: '/static/img/drawing.jpg'
        },
        {
          artTitle: 'Photography',
          image: '/static/img/photography.jpg'
        },
        {
          artTitle: 'Digital Media',
          image: '/static/img/digitalmedia.jpg'
        },
        {
          artTitle: 'Mixed Media',
          image: '/static/img/mixedmedia.jpg'
        }
      ],
      cards: []
    }
  },
  methods: {
    clickCategory (artCard) {
      this.activeButton = artCard
      this.$evt.$emit('clickCategory', {
        categoryTitle: this.activeButton.artTitle
      })
    },
    onAddFavorite (data) {
      this.$emit('addFavorite', data)
    },
    onRemoveFavorite (data) {
      this.$emit('removeFavorite', data)
    }
  },
  components: {
    Card
  }
}
</script>

<style scoped>

.Art {
  margin: auto;
  display: block;
  width: 1000px;
}

.artCard {

  border: 5px solid #7F1637;
  display: inline-block;
  margin: 20px;
  font-family: avenir;
  font-size: 28px;
  text-align: center;
  width: 250px;
  height: 250px;

}

.artCard:hover  {

background-color: #7F1637;
cursor: pointer;
}

.active {
  background-color: #7F1637;
}

.active p {
  color: white;
}

.artCard img {
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
}

.boxing {
  background-color: white;
  padding: 15px;
  border: 1px solid #ccc;
  margin: 10px;
}



</style>
