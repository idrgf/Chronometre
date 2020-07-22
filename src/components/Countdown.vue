<template>
<div>
    <h2>
      {{ timerCount }}
    </h2>
    <div v-if="timerCount == 0">
        {{ msg }}
        <br>
        {{ click }}
        <modale 
            v-bind:reveal="reveal"
            v-bind:toggleModale="toggleModale">
        </modale>
        <br>
        <button
            v-on:click="toggleModale"
            class="btn-success mt-3">
            ouvrir
        </button>
    </div>
</div>

</template>
<script>
import Modale from './Modale.vue'

export default {
    name: 'Countdown',
    data(){
        return{
            timerCount : 10,
            msg: 'Vous etes notre millième utilisateur !!!',
            click: 'Cliquez sur le bouton pour savoir ce que vous avez gagné',
            reveal: false
        }
    },
    methods: {
        toggleModale: function(){
            this.reveal = !this.reveal
        }
    },
    watch: {
        timerCount: {
            handler(timerCount) {
                if (timerCount > 0) {
                    setTimeout(() => {
                        this.timerCount--;
                    }, 1000);
                }
            },
            immediate: true 
        }
    },
    components: {
        'Modale': Modale
    }
}
</script>
<style scoped>
button{
    border-radius: 4px;
    background-color: #35495e;
    border: none
}
button:hover{
    background-color: #35495e;
}


</style>