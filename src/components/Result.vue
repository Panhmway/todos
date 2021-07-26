<template>
 
    

<div class="d-block">
   <p class="text-center">Result is {{score}} ms</p>
  <div v-if="score<250">
    <p class="text-center">You Are Too Fast!</p>
   </div>
  <div v-else-if="scor>250 && score<500">
    <p class="text-center">You Are Too Normal!</p>
   </div>
  <div v-else>
    <p class="text-center">You Are Too Slow!</p>
   </div>
</div>
 
</template>

<script>
export default {
props:['score']
}
</script>

<style>
 p{
   border-radius: 10px;
   margin-left: 38%;
   margin-right: 38%;
   padding: 10px;
   color: rgb(140, 126, 143);
   background-color: rgb(198, 198, 216);
 }
</style>