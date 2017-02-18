<!-- A fixed footer at the bottom of the screen -->
<template>
<div class="bottomFooter">
  <p>Created by:<a href="http://www.madisonwalls.org">Madison Walls</a></p>
</div>
</template>

<script>
export default {
  mounted () {
    console.log('bottomFooter -> mounted.')
  },
  beforeDestroy () {
    console.log('bottomFooter -> beforeDestroy.')
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

.bottomFooter {

  background-color: #7F1637;
  position: fixed;
  display: block;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 10px;
}

p {

  font-family: avenir;
  font-size: 14px;
  text-align: right;
  color: white;
  padding: 15px 10px;
  margin: 0px;

}

a {

  font-family: avenir;
  font-size: 14px;
  text-align: right;
  color: white;
  padding: 15px 10px;
  margin: 0px;
  text-decoration: underline;

}

</style>
