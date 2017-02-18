<template>
  <div v-show="card.Filter === title" class="Card">
  <h1>{{ card.Name }}</h1>
  <div v-show="!favoriteSelected" class="button" @click="updateValue()"><p>Favorite</p></div>
  <div v-show="favoriteSelected" class="buttonActive"><p>Added!</p></div>
  <p>{{ card.Description }}</p>
  </div>
</template>

<script>
export default {
  mounted () {
    console.log('Card -> mounted.')
    this.$evt.$on('clickCategory', this.showCard)
  },
  beforeDestroy () {
    console.log('Card -> beforeDestroy.')
  },
  props: [
    'card'
  ],
  data () {
    return {
      title: '',
      favoriteSelected: false
    }
  },
  methods: {
    showCard (data) {
      this.title = data.categoryTitle
    },
    updateValue () {
      this.favoriteSelected = true
      if (this.favoriteSelected) {
        this.$emit('addFavorite', {
          name: this.card.Name
        })
      }
    }

  }
}
</script>

<style scoped>

.Card {
margin: auto;
width: 45%;
display: inline-block;
float: right;

}

.button {
  border: 3px solid #7F1637;
  border-radius: 10px;
  display: inline-block;
  float: right;
  margin: 10px 8px;
}

.buttonActive {
  border: 3px solid #0E8C00;
  border-radius: 10px;
  display: inline-block;
  float: right;
  margin: 10px 8px;
}

.button:hover {
  background-color: rgba(127,22,55,0.5);
  cursor: pointer;
}

.button p {
  font-family: avenir;
  font-size: 10px;
  text-align: left;
  color: #7F1637;
  padding: 2px 8px;
  display: inline-block;
  float: right;
  margin: 0px;
}

.buttonActive p {
  font-family: avenir;
  font-size: 10px;
  text-align: left;
  color: #0E8C00;
  padding: 2px 8px;
  display: inline-block;
  float: right;
  margin: 0px;
}

h1 {
  font-family: carolinaCreative;
  font-size: 25px;
  text-align: left;
  text-decoration: underline;
  color: #7F1637;
  padding: 15px;
  padding-bottom: 0px;
  margin: 0px;
}

p {
  font-family: avenir;
  font-size: 14px;
  text-align: left;
  color: #7F1637;
  padding: 15px;
  padding-top: 0px;
  margin: 0px;
}

@media screen and (max-width: 460px) {
    .Card {
    margin: auto;
    width: auto;
    display: block;

    }


  }


</style>
