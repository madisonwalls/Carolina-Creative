<template>
  <div class="Favorites">
    <h1>Favorites</h1>
      <p>Welcome to Carolina Creative! The University of North Carolina at Chapel Hill offers many ways for students to explore and improve their creative skills. From beginning drawing classes to hip hop dance clubs, UNC has it all.</p>
      <p>Use the section below to look at some of the opportunities. If you like one, check the "favorite" option, and it will appear right here in this box!</p>
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

.Favorites {

border: 10px solid #7F1637;
display: inline-block;
width: 50%;

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
  font-size: 20px;
  text-align: left;
  color: #7F1637;
  padding: 25px;
  padding-top: 0px;
}

</style>
