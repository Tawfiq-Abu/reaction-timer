<template>
  <slot></slot>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
     props:['score',],
     data(){
        return{
            rank:null,
        } 
    },
    mounted(){
        console.log(this.score)
        if(this.score<250){
            this.rank = 'system overload'
        }else if(this.score<400){
            this.rank = "overrided"
        }else{
            this.rank = 'system failure'
        }
    }
}
</script>

<style scoped>
.rank {
    color:crimson;
}
</style>