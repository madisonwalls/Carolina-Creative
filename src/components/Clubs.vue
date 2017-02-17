<template>
<div class="Clubs">
  <div v-for="clubsCard in clubsCards" :class="{ 'clubsCard': true, 'active': activeButton === clubsCard }"  @click="clickCategory(clubsCard)">
    <p>{{ clubsCard.clubsTitle }}</p>
    <img v-bind:src="clubsCard.image">
  </div>
  <Card v-for="card in cards" :card="card" class="boxing" @addFavorite="onAddFavorite" @removeFavorite="onRemoveFavorite"></Card>


</div>
</template>

<script>
import axios from 'axios'
import Card from './Card'
export default {
  mounted () {
    console.log('Clubs -> mounted.')
    console.log(this.clubsCards)
    axios.get('/static/courses.json')
      .then((response) => {
        console.log(response.data)
        this.cards = response.data
      })
  },
  beforeDestroy () {
    console.log('Clubs -> beforeDestroy.')
  },
  props: [

  ],
  data () {
    return {
      activeButton: null,
      clubsCards:
      [
        {
          clubsTitle: 'Dance',
          image: '/static/img/dance.jpeg'
        },
        {
          clubsTitle: 'Comedy',
          image: '/static/img/comedy.jpeg'
        },
        {
          clubsTitle: 'Singing',
          image: '/static/img/singing.jpg'
        },
        {
          clubsTitle: 'Music',
          image: '/static/img/music.jpeg'
        },
        {
          clubsTitle: 'Club Theatre',
          image: '/static/img/theatreclub.jpg'
        },
        {
          clubsTitle: 'Club Poetry',
          image: '/static/img/poetryclub.jpg'
        }
      ],
      cards: []
    }
  },
  methods: {
    clickCategory (clubsCard) {
      this.activeButton = clubsCard
      this.$evt.$emit('clickCategory', {
        categoryTitle: this.activeButton.clubsTitle
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

.Clubs {
  margin: auto;
  display: block;
  width: 1000px;
}

.clubsCard {

  border: 5px solid #7F1637;
  display: inline-block;
  margin: 20px;
  font-family: avenir;
  font-size: 28px;
  text-align: center;
  width: 250px;
  height: 250px;

}

.clubsCard:hover  {

background-color: #7F1637;
cursor: pointer;
}

.active {
  background-color: #7F1637;
}

.active p {
  color: white;
}

.clubsCard img {
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
