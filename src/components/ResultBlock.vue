<template >
    <div>
        <p >reaction time is {{reactionTime}} ms</p>
        <p class="rank">{{ rank }}</p>
    </div>
</template>
<script>
export default {
    props:["reactionTime"],
    data(){
        return{
            rank:""
        }
    },
    mounted(){
        if(this.reactionTime<450){
            this.rank = "super fast finger"
        }else if(this.reactionTime <1000){
            this.rank = "rapid click hand"
        }else {
            this.rank = "snail pace..."
        }
    }
}
</script>
<style >
    .rank{
        font-size: 1.4em;
        color:#0faf87;
        font-weight: bold;
    }
</style>