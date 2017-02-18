<!--Shows Theatre Sub Category Cards -->
<template>
<div class="Theatre">
    <div class="cardPosition">
  <div v-for="theatreCard in theatreCards" :class="{ 'theatreCard': true, 'active': activeButton === theatreCard }"  @click="clickCategory(theatreCard)">
    <p>{{ theatreCard.theatreTitle }}</p>
    <img v-bind:src="theatreCard.image">
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
    // <!-- Tells the Filter Component which category to show -->
    clickCategory (theatreCard) {
      this.activeButton = theatreCard
      this.$evt.$emit('clickCategory', {
        categoryTitle: this.activeButton.theatreTitle
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

.Theatre {
  margin: auto;
  display: block;
  width: 1200px;
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


    .Theatre {
      margin: auto;
      display: block;
      width: 350px;
    }

    .theatreCard {

      border: 3px solid #7F1637;
      display: inline-block;
      margin: 5px;
      font-family: avenir;
      font-size: 28px;
      text-align: center;
      width: 150px;
      height: 150px;

    }

    .theatreCard img {
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
