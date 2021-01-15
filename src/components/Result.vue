<template>
  <p> Your reaction time: {{score}} ms</p>
  <p>{{result}}</p>
</template>

<script>
export default {
    props:['score'],
    data(){
      return {
          result: null,
      }
    },
    mounted() {
        if(this.score <250){
            this.result = "Ninja Fingers"
        }else if(this.score < 400){
            this.result = "Rapid reflection"
        }else{
            this.result = "Snail Pace";
        }
    },

}
</script>

<style>

</style>