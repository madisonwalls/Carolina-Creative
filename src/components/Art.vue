<!--Shows Art Sub Category Cards -->
<template>
<div class="Art">
  <div class="cardPosition">
    <div v-for="artCard in artCards" :class="{ 'artCard': true, 'active': activeButton === artCard }"  @click="clickCategory(artCard)">
      <p>{{ artCard.artTitle }}</p>
      <img v-bind:src="artCard.image">
    </div>
  </div>
  <div class="opitons" v-show="activeButton === null">
    <img src="/static/img/ccimage.png">
      <h1>Pick a Sub Category to View Options</h1>
  </div>
  <Card v-for="card in cards" :card="card" class="boxing" @addFavorite="onAddFavorite"></Card>
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
        },
        {
          artTitle: 'Printmaking',
          image: '/static/img/printmaking.JPG'
        }
      ],
      cards: []
    }
  },
  methods: {
    // <!-- Tells the Filter Component which category to show -->
    clickCategory (artCard) {
      this.activeButton = artCard
      this.$evt.$emit('clickCategory', {
        categoryTitle: this.activeButton.artTitle
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

.Art {
  margin: auto;
  display: block;
  width: 1200px;

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

@media screen and (max-width: 460px) {


    .Art {
      margin: auto;
      display: block;
      width: 350px;
    }

    .artCard {

      border: 3px solid #7F1637;
      display: inline-block;
      margin: 5px;
      font-family: avenir;
      font-size: 28px;
      text-align: center;
      width: 150px;
      height: 150px;

    }

    .artCard img {
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
      margin: auto 25px;
      display: block;
      text-align: center;
      position: absolute;
    }

    img {
      opacity: 0;
    }

    h1 {
      display: none;
    }

  }


</style>
