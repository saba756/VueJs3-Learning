<template>
  <div class="hello">
    <!-- <h1>{{msg}}</h1>
    <input v-model="value"
    type="checkbox"
    value="a"
    />
       <input v-model="value"
    type="checkbox"
    value="b"
    />
    {{value}}
    <div class="red">{{error}}</div> -->
<!-- <h3>V-if,else,for</h3>
 <button v-on:click="increment">Increment</button>
<p>{{count}}</p> -->


<!-- <h3>Computed properties</h3>
<div v-for="num in evenList" v-bind:key="num.id">
  <p>{{num}} </p>

</div> -->
<Number 
v-for="num in numbers" v-bind:key="num.id"
v-bind:num="num"
v-on:chosen="addNumber"
/>
<hr/>
<Number 
v-for="num in historyNumber" v-bind:key="num.id"
v-bind:num="num"

/>
  </div>
</template>

<script>
import Number from './Number.vue';
export default {
  name: 'HelloWorld',
  components:{
    Number
    },
  props:{
    msg:String
  },
  data(){
    return {
      count: 0,
      value: ["a"],
      numbers:[1,2,3,4,5,6,7,8,9,10],
      historyNumber:[]
    
    }
  },
  computed :{
    evenList(){
      return this.numbers.filter(num => this.isEven(num));
      },
      error(){
      if(this.value.length < 5){
       return 'Must be greater than five';
      }
      else{
        return '';
      }}
      },

  methods:{
    increment(){
      this.count +=1
  },
addNumber(num){
  this.historyNumber.push(num)
console.log("num",num)
  }
  }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.blue{
  color: blue;
  }
.red{
  color: red
  }
</style>
