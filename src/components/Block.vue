<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      click me
  </div>
</template>

<script>
export default {
    props:['delay',],
    data() {
        return {
            showBlock: false,
            timer:null,
            reactionTimer:0
        }
    },
    mounted(){
     setTimeout(()=>{
         this.showBlock = true
         this.startTimer()
     },this.delay)
    },
    methods: {
        startTimer(){
            this.timer = setInterval(()=>{
                this.reactionTimer +=10
            },10)
        },
        stopTimer(){
           clearInterval(this.timer) 
            //create a custom event and send the reaction timer data with it
            this.$emit('end',this.reactionTimer) 
        }
    },
    
}
</script>

<style>
.block{
    width:400px;
    border-radius:20px;
    background-color:aqua;
    color:white;
    text-align:center;
    padding:100px 0;
    margin:40px auto;
}
</style>