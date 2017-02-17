<template>
  <div v-show="card.Filter === title" class="Card">
  <h1>{{ card.Name }}</h1>
  <input type="checkbox" v-model="favoriteSelected" @change="updateValue">
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
      console.log(data.categoryTitle)
      this.title = data.categoryTitle
    },
    updateValue () {
      console.log(this.favoriteSelected)
      if (this.favoriteSelected) {
        this.$emit('addFavorite', {
          name: this.card.Name
        })
      } else {
        this.$emit('removeFavorite')
      }
    }
  }
}
</script>

<style scoped>

.Card {

margin: auto;
width: 840px;
display: block;


}

input {
  float: right;
  display: block;
  border: solid, #7F1637;

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

</style>
