<!-- Displays opening information/credit and updates automatically with the user's favorite selections -->
<template>
<div class="favoritesBox">
  <div class="Favorites">
    <h1>Favorites</h1>
      <p v-show="this.favorites.length <= 0 ">Welcome to Carolina Creative! The University of North Carolina at Chapel Hill offers many ways for students to explore and improve their creative skills. From beginning drawing classes to hip hop dance clubs, UNC has it all.</p>
      <p v-show="this.favorites.length <= 0 ">Use the section below to look at some of the opportunities. If you like one, check the "favorite" option, and it will appear right here in this box!</p>
      <h2 v-show="this.favorites.length <= 0 ">Credit:</h2>
      <p v-show="this.favorites.length <= 0 ">All information was gathered from <a href="https://studentlife.unc.edu/">Studentlife.unc.edu</a> and <a href="http://www.catalog.unc.edu/">The Undergraduate Academic Catalog</a>. Images are free stock photos from <a href="https://www.pexels.com">Pexels</a> and video content is original work.</p>
    </div>
  <div v-for="(favorite, index) in favorites">
    <p class="addedFavorite">{{ favorite.name }}</p>
    <div class="button" @click="remove(index)"><p>Remove</p></div>
  </div>
</div>
</template>

<script>
export default {
  mounted () {
    console.log('Favorites -> mounted.')
  },
  beforeDestroy () {
    console.log('Favorites -> beforeDestroy.')
  },
  props: [
    'favorites'
  ],
  data () {
    return {
    }
  },
  methods: {
    // <!-- Removes Favorite -->
    remove (i) {
      this.favorites.splice(i, 1)
      console.log(i)
    }
  }
}
</script>

<style scoped>

.favoritesBox{
  margin: auto;
  display: inline-block;
  width: 400px;
  height: 420px;
  border: 10px solid #7F1637;
  margin-top: 10px;
  margin-bottom: 40px;
  overflow: scroll;

}


h1 {
  font-family: carolinaCreative;
  font-size: 45px;
  text-align: center;
  text-decoration: underline;
  color: #7F1637;
  margin-top: 5px;
}

p {
  font-family: avenir;
  font-size: 14px;
  text-align: left;
  color: #7F1637;
  padding: 15px 10px;
  margin: 0px;

}

h2 {
  font-family: avenir;
  font-weight: bold;
  font-size: 14px;
  text-align: left;
  color: #7F1637;
  padding-left: 10px;
  margin: 0px;

}

a {
  text-decoration: none;
  font-weight: bold;
  color: #420B1D;
}

.button {
  border: 3px solid #7F1637;
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

.addedFavorite {
  display: inline-block;
  width: 300px;
}

@media screen and (max-width: 460px) {
      .favoritesBox {
        margin: auto;
        display: block;
        width: 330px;
        border: 5px solid #7F1637;
        height: 350px;
      }
  }

</style>
