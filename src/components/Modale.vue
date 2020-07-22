<template>
<div
    v-if="reveal"
    class="bloc-modale">
        <div
            class="overlay">
                <div class="modale card mt-4">
                    <div
                        v-on:click="toggleModale"
                        class="btn-modale btn btn-danger">x
                    </div>
                    <h2>{{ MessageModale }}</h2>
                </div>
        </div> 
</div>
</template>
<script>
export default {
    name: 'Modale',
    data(){
        return{
            MessageModale: 'Ne jamais cliquer sur ce bouton --\''
        }
    },
    props: ['reveal', 'toggleModale']
}


</script>
<style>
    .block-modale{
        position: fixed;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        width: 100%;
        height: 100%;
        
    }
    .overlay{
        background-color: rgba(53, 73, 94, 0.9);
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .modale{
        padding: 50px;
        width: 50%;
    }
    .btn-modale{
        position: absolute;
        top: 10px;
        right: 10px;
        padding: 0;
    }

</style>