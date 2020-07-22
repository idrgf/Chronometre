<template>
  <div class="container">
    <h1>Chronometre</h1>
    <div class="bgc">
      <h1>
        <span class="label label-primary">{{minutes}}</span> :
        <span class="label label-primary">{{secondes}}</span>
      </h1>
      

      <button
        class="btn btn-primary mr-4"
        v-show="startShow"
        v-on:click="start">
        start
      </button>


      <button 
          class="btn btn-primary mr-4"
          v-show="stopShow"
          v-on:click="stop">
          stop
      </button>
      

      <button class="btn btn-primary"
          v-on:click="reset">
          reset
      </button>
    </div>

    <countdown></countdown>

    

    
  </div>
  
</template>

<script>
import Countdown from './Countdown.vue'

export default {
  name: 'Chrono',
  data() {
    return {
      minutes: 0,
      secondes: 0,
      totalSecondes: 0,
      timer:'',
      startShow: true,
      stopShow: false
    }
  },
  methods: {
    start: function() {
      var ctx = this;
      
      ctx.startShow = false;
      ctx.stopShow = true;

      ctx.timer = setInterval(function() {
        
      ctx.totalSecondes++;
      
      ctx.minutes = Math.floor(ctx.totalSecondes /60);

      //mise à jour des secondes
      ctx.secondes = ctx.totalSecondes - ctx.minutes * 60;

      }, 1000)
    },
    stop: function() {
      clearInterval(this.timer)
      this.startShow = true,
      this.stopShow = false
    },
    reset: function () {
      clearInterval(this.timer),
      this.heures = 0,
      this.minutes = 0,
      this.secondes = 0,
      this.totalSecondes = 0,
      this.startShow = true,
      this.stopShow = false
    }
  },
  components: {
    'Countdown': Countdown
  }
}
</script>
<style>
 .bgc{
    padding: 20px;
    width: 300px;
    background-color: #41b883;
    margin: 30px auto;
    border: 1px solid #000;
    border-radius: 7px
 }

</style>