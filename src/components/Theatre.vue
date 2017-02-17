<template>
<div class="Theatre">
  <div v-for="theatreCard in theatreCards" :class="{ 'theatreCard': true, 'active': activeButton === theatreCard }"  @click="clickCategory(theatreCard)">
    <p>{{ theatreCard.theatreTitle }}</p>
    <img v-bind:src="theatreCard.image">
  </div>
  <Card v-for="card in cards" :card="card" class="boxing" @addFavorite="onAddFavorite" @removeFavorite="onRemoveFavorite"></Card>


</div>
</template>

<script>
import axios from 'axios'
import Card from './Card'
export default {
  mounted () {
    console.log('Theatre -> mounted.')
    console.log(this.theatreCards)
    axios.get('/static/courses.json')
      .then((response) => {
        console.log(response.data)
        this.cards = response.data
      })
  },
  beforeDestroy () {
    console.log('Theatre -> beforeDestroy.')
  },
  props: [

  ],
  data () {
    return {
      activeButton: null,
      theatreCards:
      [
        {
          theatreTitle: 'Acting',
          image: '/static/img/acting.jpg'
        },
        {
          theatreTitle: 'Drama',
          image: '/static/img/drama.JPG'
        },
        {
          theatreTitle: 'Theatre',
          image: '/static/img/theatre.jpg'
        },
        {
          theatreTitle: 'Play Writing',
          image: '/static/img/playwriting.jpeg'
        }
      ],
      cards: []
    }
  },
  methods: {
    clickCategory (theatreCard) {
      this.activeButton = theatreCard
      this.$evt.$emit('clickCategory', {
        categoryTitle: this.activeButton.theatreTitle
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

.Theatre {
  margin: auto;
  display: block;
  width: 1000px;
}

.theatreCard {

  border: 5px solid #7F1637;
  display: inline-block;
  margin: 20px;
  font-family: avenir;
  font-size: 28px;
  text-align: center;
  width: 250px;
  height: 250px;

}

.theatreCard:hover  {

background-color: #7F1637;
cursor: pointer;
}

.active {
  background-color: #7F1637;
}

.active p {
  color: white;
}

.theatreCard img {
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
