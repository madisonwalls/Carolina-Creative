<template>
<div class="Writing">
  <div v-for="writingCard in writingCards" :class="{ 'writingCard': true, 'active': activeButton === writingCard }"  @click="clickCategory(writingCard)">
    <p>{{ writingCard.writingTitle }}</p>
    <img v-bind:src="writingCard.image">
  </div>
  <Card v-for="card in cards" :card="card" class="boxing" @addFavorite="onAddFavorite" @removeFavorite="onRemoveFavorite"></Card>


</div>
</template>

<script>
import axios from 'axios'
import Card from './Card'
export default {
  mounted () {
    console.log('Writing -> mounted.')
    console.log(this.writingCards)
    axios.get('/static/courses.json')
      .then((response) => {
        console.log(response.data)
        this.cards = response.data
      })
  },
  beforeDestroy () {
    console.log('Writing -> beforeDestroy.')
  },
  props: [

  ],
  data () {
    return {
      activeButton: null,
      writingCards:
      [
        {
          writingTitle: 'Fiction',
          image: '/static/img/fiction.jpg'
        },
        {
          writingTitle: 'Poetry',
          image: '/static/img/poetry.png'
        },
        {
          writingTitle: 'Other',
          image: '/static/img/other.jpeg'
        }
      ],
      cards: []
    }
  },
  methods: {
    clickCategory (writingCard) {
      this.activeButton = writingCard
      this.$evt.$emit('clickCategory', {
        categoryTitle: this.activeButton.writingTitle
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

.Writing {
  margin: auto;
  display: block;
  width: 1000px;
}

.writingCard {

  border: 5px solid #7F1637;
  display: inline-block;
  margin: 20px;
  font-family: avenir;
  font-size: 28px;
  text-align: center;
  width: 250px;
  height: 250px;

}

.writingCard:hover  {

background-color: #7F1637;
cursor: pointer;
}

.active {
  background-color: #7F1637;
}

.active p {
  color: white;
}

.writingCard img {
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
