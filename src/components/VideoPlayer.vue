<!-- Displays the video at the top of the page -->
<template>
<div class="videoBox">
    <div class="VideoPlayer">
    <iframe src="https://player.vimeo.com/video/203925933" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
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
width: 730px;
height: 420px;
margin: 10px;
float: left;


}

iframe {
  width: 730px;
  height: 420px;
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

@media screen and (max-width: 460px) {
    .VideoPlayer {
      width: 330px;
      height: 200px;
      border: 5px solid #7F1637;

    }
    iframe {
      width: 330px;
      height: 200px;
    }
}

</style>
