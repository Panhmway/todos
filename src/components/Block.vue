<template>
  <div class="block" v-if="showBlock" @click="stopTimer"> </div>
</template>

<script>
export default {
props:['delay'],
data() {
    return {
        showBlock:false,
        score:0,
        timer:null
    }
    
},
    mounted() {
        setTimeout(()=>{
            this.showBlock=true;
            this.startTimer()
        },this.delay);
    },
    methods: {
        startTimer(){
          this.timer=setInterval(()=>{
                this.score+=50;
            },50);
        },
        stopTimer(){
            clearInterval(this.timer); 
           this.$emit("endGame",this.score)
        }
    },
}
</script>

<style>
.block{
    background-color: #85FFBD;
    background-image: linear-gradient(45deg, #85FFBD 0%, #FFFB7D 100%);
    width: 400px;
    height: 200px;
    margin: 20px auto;
    padding-top: 40px;
    border-radius:30px;
}
</style>