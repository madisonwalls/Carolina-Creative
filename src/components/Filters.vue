<template>
  <div class="Filters">

    <div v-for="button in buttons" :class="{ 'button': true, 'active': activeButton === button }" @click="clickButton(button)">{{ button.titleContent }}</div>


  </div>
</template>

<script>
export default {
  mounted () {
    console.log('Filters -> mounted.')
    console.log('buttons', this.buttons)
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
          titleContent: 'Art'
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
          titleContent: 'All'
        }

      ]
    }
  },
  methods: {
    clickButton (button) {
      this.activeButton = button
    }
  }
}
</script>

<style scoped>

.button {

border: 3px solid #7F1637;
display: inline-block;
margin: 10px;
font-family: avenir;
font-size: 14px;
text-align: left;
color: #7F1637;
padding: 10px 40px;
cursor: pointer;


}
.active {
background-color: #7F1637;
color: white;
display: inline-block;
margin: 10px;
font-family: avenir;
font-size: 14px;
text-align: left;
padding: 10px 40px;
}


.Filters {

display: inline-block;
margin-bottom: 25px;
margin-left: 80px;

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
  font-size: 14px;
  text-align: left;
  color: #7F1637;
  padding: 5px 50px;

}

</style>
