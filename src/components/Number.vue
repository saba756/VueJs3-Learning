<template>
<div>
<button 
   v-bind:class="getClass(num)"
   v-on:click="click(num)">
   {{num}}
  <!-- <span v-if="Even(num)">Even</span>
    <span v-else>Odd</span> -->
 </button>
</div>
</template>

<script>


export default {
  name: 'Number',
    props:{
    num:Number
  },
 
 methods:{
     click(){
         this.$emit('chosen',this.num)
       
     },
    getClass(num){
      return this.isEven(num) ? 'blue': 'red';
    },
    isEven(num){
   return num%2 === 0;
  
  }
}
}
</script>
<style scoped>
.blue{
  color: blue;
  }
.red{
  color: red
  }
</style>

