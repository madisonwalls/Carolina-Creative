<template>
  <div>
  <div class="Filters">
    <div v-for="button in buttons" :class="{ 'button': true, 'active': activeButton === button }" @click="clickButton(button)">{{ button.titleContent }}</div>
  </div>
  <div  v-show="activeButton === null">
  <img src="/static/img/ccimage.png">
  <h1>Select a Tab Above</h1>
  </div>
</div>
</template>

<script>
import All from './All'
export default {
  mounted () {
    console.log('Filters -> mounted.')
    console.log('buttons', this.buttons)
    console.log(this.filtername)
  },
  beforeDestroy () {
    console.log('Filters -> beforeDestroy.')
  },
  props: [
  ],
  data () {
    return {
      activeButton: null,
      buttons: [
        {
          titleContent: 'All'
        },
        {
          titleContent: 'Music'
        },
        {
          titleContent: 'Writing'
        },
        {
          titleContent: 'Theatre'
        },
        {
          titleContent: 'Clubs'
        },
        {
          titleContent: 'Art'
        }

      ]
    }
  },
  methods: {
    clickButton (button) {
      this.activeButton = button
      console.log(this.activeButton.titleContent)
      this.$evt.$emit('clickButton', {
        newTab: this.activeButton.titleContent
      })
    }
  },
  components: {
    All
  }
}
</script>

<style scoped>

.button {

border: 3px solid #7F1637;
display: inline-block;
margin: 10px;
font-family: avenir;
font-size: 18px;
text-align: center;
color: #7F1637;
cursor: pointer;
margin-bottom: 40px;
width: 120px;
height: 30px;
padding-top: 10px;
}

.button:hover {
  background-color: rgba(127,22,55,0.5);
  cursor: pointer;
}

.active {
background-color: #7F1637;
color: white;
display: inline-block;
margin: 10px;
font-family: avenir;
font-size: 18px;
text-align: center;
cursor: pointer;
margin-bottom: 40px;
width: 120px;
height: 30px;
padding-top: 10px;
}


.Filters {

display: block;
margin: auto;
width: 950px;

}

h1 {
  font-family: carolinaCreative;
  font-size: 65px;
  text-align: center;
  color: #7F1637;
  padding: 15px;
  padding-top: 100px;
  position: relative;
}

p {
  font-family: avenir;
  font-size: 14px;
  text-align: left;
  color: #7F1637;
  padding: 5px 50px;

}

img {
  width: 1200px;
  height: auto;
  display: block;
  margin: auto;
  opacity: 0.3;
  position: absolute;
}

@media screen and (max-width: 460px) {

    .Filters {
    display: block;
    margin: auto;
    width: 260px;
    }

    .button {

    border: 2px solid #7F1637;
    display: inline-block;
    margin: 5px;
    font-family: avenir;
    font-size: 18px;
    text-align: center;
    color: #7F1637;
    width: 240px;
    height: 30px;
    cursor: pointer;
    margin-bottom: 10px;
    }

    .active {
    background-color: #7F1637;
    color: white;
    }

    img, h1 {
      display:none;
    }

  }

</style>
