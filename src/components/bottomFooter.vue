<template>
<div class="bottomFooter">
  <p>Madison Walls</p>
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
  position: inherit;
  display: block;
  right: 0;
  bottom: 0;
  left: 0;
}

p {

  font-family: avenir;
  font-size: 14px;
  text-align: left;
  color: white;
  padding: 15px 10px;
  margin: 0px;

}

</style>
