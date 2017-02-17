<template>
<div class="Footer">
  <p>Madison Walls</p>
</div>
</template>

<script>
export default {
  mounted () {
    console.log('Footer -> mounted.')
  },
  beforeDestroy () {
    console.log('Footer -> beforeDestroy.')
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

p {

  font-family: avenir;
  font-size: 14px;
  text-align: left;
  color: #7F1637;
  padding: 15px 10px;
  margin: 0px;

}

</style>
