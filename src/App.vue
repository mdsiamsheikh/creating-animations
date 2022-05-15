<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1 class="text-center">The Super Quiz</h1>
            </div>
        </div>
        <hr>
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
              <transition name="flip" mode="out-in">
               <component :is="mode" @answered="answered($event)" @confirmed="mode = 'app-queStion'"></component>
              </transition>  
            </div>
        </div>
    </div>
</template>

<script>
   import QueStion from "./components/QueStion.vue";
   import AnsWer from "./components/AnsWer.vue";

    export default {
          data() {
            return {
              mode: 'app-queStion'
            }
          },
          methods: {
              answered(isCorrect) {
                if (isCorrect) {
                  this.mode = 'app-ansWer';
                } else {
                  this.mode = 'app-queStion';
                  alert('Wrong, try again!');
                }
              }
          },
          components: {
            appQueStion: QueStion,
            appAnsWer: AnsWer
          }
    }
</script>

<style>
   .flip-enter {
     /* transform: rotateY(0deg); */
   }

   .flip-enter-active {
      animation: flip-in 0.5s ease-out forwards;
   }

   .flip-leave {
       /* transform: rotateY(0deg); */
   }

   .flip-leave-active {
     animation: flip-out 0.5s ease-out forwards;
   }

   @keyframes flip-out {
     from {
       transform: rotateY(0deg);
     }
     to {
       transform: rotateY(90deg);
     }
   }

    @keyframes flip-in {
     from {
       transform: rotateY(90deg);
     }
     to {
       transform: rotateY(0deg);
     }
   }
</style>

