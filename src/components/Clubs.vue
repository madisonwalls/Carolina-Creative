<template>
<div class="Clubs">
  <div class="cardPosition">
  <div v-for="clubsCard in clubsCards" :class="{ 'clubsCard': true, 'active': activeButton === clubsCard }"  @click="clickCategory(clubsCard)">
    <p>{{ clubsCard.clubsTitle }}</p>
    <img v-bind:src="clubsCard.image">
  </div>
</div>
  <Card v-for="card in cards" :card="card" class="boxing" @addFavorite="onAddFavorite" @removeFavorite="onRemoveFavorite"></Card>
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
  width: 1200px;
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


    .Clubs {
      margin: auto;
      display: block;
      width: 350px;
    }

    .clubsCard {

      border: 3px solid #7F1637;
      display: inline-block;
      margin: 5px;
      font-family: avenir;
      font-size: 28px;
      text-align: center;
      width: 150px;
      height: 150px;

    }

    .clubsCard img {
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
