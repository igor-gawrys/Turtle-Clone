<template>

  <div>
    
     <div class='form-group'> 

       <input type="text" placeholder="Komenda!" class="form-control"  @keyup.enter="enter" />

     </div>

     <div class='btn-group' >

        <button class='btn btn-success' disabled> W przód </button>

        <button class='btn btn-danger' @click="backwards( )"> W tył </button>

     </div>

  </div>

</template>

<script>

 export default {

    data() {

      return {

        history: [

            {

               position: [ 30, 30, 20, 20 ],

               color: "#fff",

               mode: "move"

            }
            
        ]

      }

    },

    methods: {

      enter( e ) {

         this.$emit( 'entered', e.srcElement.value, this.history );

         e.srcElement.value = "";

      },

      backwards( ) {

         this.$emit( 'backwards', this.history );

      }

    }

 }

</script>

<style>

</style>

