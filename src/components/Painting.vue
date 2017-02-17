<template>
<div class="Painting">
  <ul>
    <li v-for="">hey</li>
  <ul>
</div>
</template>

<script>

export default {
  mounted () {
    console.log('Painting -> mounted.')
  },
  beforeDestroy () {
    console.log('Painting -> beforeDestroy.')
  },
  props: [

  ],
  data () {
    return {
      content: []
    }
  },
  methods: {
  }
}
</script>

<style scoped>


</style>
