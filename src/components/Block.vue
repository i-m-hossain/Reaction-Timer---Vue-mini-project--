<template>
  <div id="block" v-if="showBlock" @click="stopTimer">
      click me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return{
            showBlock: false,
            timer: null,
            reactionTime:0
        }
    },
    methods: {
        startTimer(){
            this.timer = setInterval(()=>{
                this.reactionTime += 10    
            },10)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('end',this.reactionTime)
          
            
        }
        
    },
    mounted(){
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay);
    }

}
</script>

<style>
    #block{
        margin: 20px auto;
        width:400px;
        padding: 100px 0;
        background: rgba(52, 185, 112, 0.829);
        color:#002123

    }
</style>