<template>
  <p>Reaction Time - {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data(){
        return{
            rank: null
        }
    },
    mounted(){
        if(this.score < 250){
            this.rank = 'Usain Bolt Speed!'
        } else if(this.score < 400){
            this.rank = 'Fast Reaction'
        } else{
            this.rank = 'Too slow....'
        }
    }
}
</script>

<style>
    .rank{
        font-size: 1.4em;
        color: teal;
        font-weight: bold;
    }

</style>