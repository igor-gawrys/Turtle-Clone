<template>
  <div>
  
     <canvas ref="container" ></canvas>

  </div>
</template>

<script>

 export default {

  data() {

    return {

      provider: {
      
        context: null

      }

    }

  },

  provide () {

    return {

      provider: this.provider

    }

  },

  mounted () {
  
    this.provider.context = this.$refs['container'].getContext('2d')

    this.$refs['container'].width = 400;

    this.$refs['container'].height = 400;

    this.provider.context.beginPath();

    this.provider.context.moveTo( 0, 0 );

    this.provider.context.fillRect( 30, 30, 20, 20 );

    this.provider.context.fill();

    // this.provider.context.clearRect( 0, 0, 400, 400 );this.provider.context.clearRect( 0, 0, 400, 400 );

  }

 }

</script>

<style scoped>

 div {

   margin-left: 10vh;

 }

 canvas {

  border: 4px solid black;

 }

</style>

