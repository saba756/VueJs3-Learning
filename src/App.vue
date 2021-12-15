<template>
<div>
   <button @click="a++">{{a}}</button>

  <button @click="b++">{{b}}</button>
  <p>{{total}}</p>
  <div v-for="number in history" :key="number.id">
    {{number}}
  </div>
</div>
</template>

<script>

import { useNumbers } from './components/UseNumber'

export default {
 setup(){
   //ref is used for primitive values like num, string etc
 
   //reactive is used for complex values array, objects etc
  //  const numbers = reactive({
  //    a:0,
  //    b:0
  //  })

 
  //  const increase =(n)=>{
  //    numbers[n]++
  //  }
   //if any change in count , a and b it update the  dom according to that
   
  const {a, b,double, history} = useNumbers()


   return {
      a, b, history,double
    }
 }
}
</script>

<style scoped>
p{
  font-size: 40px;
}
button{
  height: 200px;
  width:200px;
  font-size: 40px;
}
</style>
