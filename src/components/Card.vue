<template>
  <div class="Card">
  <h1>{{ card.Filter }}</h1>
  </div>
</template>

<script>
export default {
  mounted () {
    console.log('Card -> mounted.')
  },
  beforeDestroy () {
    console.log('Card -> beforeDestroy.')
  },
  props: [
    'card'
  ],
  data () {
    return {
    }
  },
  methods: {

  }
}
</script>

<style scoped>

.Card {

border: 10px solid #7F1637;
display: block;




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
  padding: 25px;
  padding-top: 0px;
}

</style>
