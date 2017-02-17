<template>
<div class="videoBox">
    <div class="VideoPlayer">
    <iframe src="https://player.vimeo.com/video/203925933" width="660" height="380" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
    </div>
</div>
</template>

<script>
export default {
  mounted () {
    console.log('VideoPlayer -> mounted.')
  },
  beforeDestroy () {
    console.log('VideoPlayer -> beforeDestroy.')
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

.VideoPlayer {

border: 10px solid #7F1637;
display: inline-block;
width: 660px;
height: 380px;
margin: 10px;
float: left;


}

.videoBox {
  margin: auto;
  display: block;
  width: 1200px;
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

.player .video-wrapper video {
    width: 100%;
    height: auto;
}

</style>
