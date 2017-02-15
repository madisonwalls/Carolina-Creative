<template>
<div class="Art">
  <div v-for="artCard in artCards" class="ArtBox">
    <p>{{ artCard.artTitle }}</p>
    <img v-bind:src="artCard.image">
  </div>

</div>
</template>

<script>
export default {
  mounted () {
    console.log('Art -> mounted.')
    console.log(this.artCards)
  },
  beforeDestroy () {
    console.log('Art -> beforeDestroy.')
  },
  props: [

  ],
  data () {
    return {
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
      ]
    }
  },
  methods: {
  }
}
</script>

<style scoped>

.Art {
  margin: auto;
  display: block;
  width: 1000px;
}

.ArtBox {

  border: 5px solid #7F1637;
  display: inline-block;
  margin: 20px;
  font-family: avenir;
  font-size: 28px;
  text-align: center;
  width: 250px;
  height: 250px;

}

.ArtBox:hover {

background-color: #7F1637;
cursor: pointer;
color: white;

}

.ArtBox img {
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



</style>
