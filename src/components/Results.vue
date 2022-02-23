<template>
    <div>
          <p >Reaction Time {{score}} ms  </p>
          <p class="rank"> {{rank}} </p>

    </div>
</template>
<script>
export default {
    props:{
        score:{
            type:Number,
            required:true
        }
    },
    data() {
        return {
            rank:null
        }
    },
    mounted() {
        if(this.score < 250){
            this.rank = 'You are so fast!'
        }
        else if(this.score < 400){
            this.rank = 'Rapid Reflex!'
        }
        else{
            this.rank = 'Slow asf)'
        }
    },
    
}
</script>
<style scoped>
    .rank{
        font-size: 1.4em;
        color: #040404;
        font-weight: 500;
    }
</style>