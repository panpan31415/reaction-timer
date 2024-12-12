<template>
    <div class="block" v-if="showBlock" @click="closeBlock">
        click me
    </div>
    <div class="wait" v-if="!showBlock" >
        Are you ready ...... ?
    </div>
</template>
<script>
export default {
    props:["delay"],
    data:function(){
        return {
            showBlock:false,
            timerId:null,
            mountedAt:0,
           
        }
    },
    methods:{
        closeBlock(){
            const reactedAt = new Date().getTime()
            const reactionTime  = reactedAt - this.mountedAt;
            console.log("reactionTime is:"+ reactionTime + "ms")
            this.$emit("closeBlock",{reactionTime})
        }
    },
    mounted(){
    this.timerId = setTimeout(() => {
        this.showBlock = true;
        this.mountedAt = new Date().getTime();
    }, this.delay);
  },
  beforeUnmount(){
    if(this.timerId){
        clearTimeout(this.timerId);
        this.timerId = null;
    }
  }
}
</script>
<style>
    .block{
        width: 400px;
        border-radius: 20px;
        background-color: #0faf87;
        color: white;
        text-align: center;
        font-weight: bold;
        padding: 100px 0;
        margin: 40px auto;
    }

    .wait{
        width: 400px;
        border-radius: 20px;
        border:2px solid #0faf87;
        color: #0faf87;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>