<template>

  <section class="container">

   <div class='row'>

    <div class='col-md-6' >
      
        <AppCommander ref="commander" v-on:entered="entered" >

        </AppCommander>

    </div>

    <div class='col-md-6' >
      
        <AppContainer ref="provider" >

        </AppContainer>
    
    </div>
   </div>
  </section>
  
</template>

<script>

import AppContainer from '~/components/AppContainer.vue'

import AppCommander from '~/components/AppCommander.vue'

export default {

  components: {
    AppContainer,
    AppCommander
  },

  data() {

    return {

    }

  },
  
  methods: {
 
     entered( e, history ) {

       let position = history [ history.length - 1 ].position;

       let value;

       switch( e ) {

          case "mode move":

           alert( "Ustawiłem tryb MOVE!" );

           history.push( {

              position: position,

              color: history [ history.length - 1 ],

              mode: "move"

           } );

           this.$emit( 'history', history );

          break;

          case "mode draw":

           alert( "Ustawiłem tryb DRAW!" );

           history.push( {

              position: position,

              color: history [ history.length - 1 ],

              mode: "draw"

           } );

           this.$emit( 'history', history );

          break;

          case ( e.match( "move:bottom (.*)" )  || {} ).input:

           value = e.match( "move:bottom (.*)" ) [ 1 ];

          if( position [ 1 ] - value / 10 != 0 && position [ 1 ] - value / 10 > 0 ) { 

           this.$refs[ 'provider' ].provider.context.clearRect( position [ 0 ], position [ 1 ], position [ 2 ], position [ 3 ] );

           this.$refs[ 'provider' ].provider.context.fillRect( position [ 0 ], position [ 1 ] + value / 10, position [ 2 ], position [ 3 ] );

           this.$refs[ 'provider' ].provider.context.fillStyle = history.color;

           this.$refs[ 'provider' ].provider.context.fill();

           history.push( {

              position: [

                  position [ 0 ],

                  position [ 1 ] + value / 10,

                  position [ 2 ],

                  position [ 3 ]

              ],
              color: history [ history.length - 1 ].color

           } );

           this.$emit( 'history', history );

          }

          break;

          case "move:top":

            alert( "Podaj argument!" );

          break;

          case ( e.match( "move:top (.*)" )  || {} ).input:

           value = e.match( "move:top (.*)" ) [ 1 ];
          
          if( position [ 1 ] - value / 10 != 0 && position [ 1 ] - value / 10 > 0 ) { 

           this.$refs[ 'provider' ].provider.context.clearRect( position [ 0 ], position [ 1 ], position [ 2 ], position [ 3 ] );

           this.$refs[ 'provider' ].provider.context.fillRect( position [ 0 ], position [ 1 ] - value / 10, position [ 2 ], position [ 3 ] );

           this.$refs[ 'provider' ].provider.context.fillStyle = history.color;

           this.$refs[ 'provider' ].provider.context.fill();

           history.push( {

              position: [

                  position [ 0 ],

                  position [ 1 ] - value / 10,

                  position [ 2 ],

                  position [ 3 ]

              ],
              color: history [ history.length - 1 ].color

           } );

           this.$emit( 'history', history );

          }

          break;

          case "move:bottom":

            alert( "Podaj argument!" );

          break;

          case "move:top":

            alert( "Podaj argument!" );

          break;

          case ( e.match( "move:right (.*)" )  || {} ).input:

           value = e.match( "move:right (.*)" ) [ 1 ];
          
          if( position [ 0 ] + value / 10 != 0 && position [ 0 ] + value / 10 > 0 ) { 

           this.$refs[ 'provider' ].provider.context.clearRect( position [ 0 ], position [ 1 ], position [ 2 ], position [ 3 ] );

           this.$refs[ 'provider' ].provider.context.fillRect( position [ 0 ] + value / 10, position [ 1 ], position [ 2 ], position [ 3 ] );

           this.$refs[ 'provider' ].provider.context.fillStyle = history.color;

           this.$refs[ 'provider' ].provider.context.fill();

           history.push( {

              position: [

                  position [ 0 ] + value / 10,

                  position [ 1 ],

                  position [ 2 ],

                  position [ 3 ]

              ],
              color: history [ history.length - 1 ].color

           } );

           this.$emit( 'history', history );

          }

          break;

          case "move:right":

            alert( "Podaj argument!" );

          break;

          case ( e.match( "move:color (.*)" )  || {} ).input:

           value = e.match( "move:color (.*)" ) [ 1 ];

           this.$refs[ 'provider' ].provider.context.clearRect( position [ 0 ], position [ 1 ], position [ 2 ], position [ 3 ] );

           this.$refs[ 'provider' ].provider.context.fillRect( position [ 0 ], position [ 1 ], position [ 2 ], position [ 3 ] );

           this.$refs[ 'provider' ].provider.context.fillStyle = value;

           this.$refs[ 'provider' ].provider.context.fill();

           history.push( {

              position: [

                  position [ 0 ],

                  position [ 1 ],

                  position [ 2 ],

                  position [ 3 ]

              ],
              color: value

           } );

           this.$emit( 'history', history );

          break;

          case "move:color":

            alert( "Podaj argument!" );

          break;

          default:

            alert( "Oh !, ta komenda nie istnieje :(" );
            
          break;

       }

       this.$refs[ 'commander' ].history = history;

     }

  }
}
</script>

<style lang="scss" >

@import 'node_modules/bootstrap/scss/bootstrap';

@import 'node_modules/bootstrap-vue/src/index.scss';

@import '~/assets/scss/app.scss';

.container {

  margin-top: 5vh;

}

</style>

