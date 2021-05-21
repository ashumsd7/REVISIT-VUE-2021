<template>
  <div class="hello">
    {{randomNumber}}
    {{ Math.random() }}
    <p v-html="htmlData"> </p>
    <a v-bind:href="myLink" target="_blank" rel="noopener noreferrer"> Dynamic Link (href frim data section) Go to google </a>
    <hr>
    <button  v-on:click="executeMethod()">Click Me</button>
    <hr>
    <small>>>>>Event Listner Parameters</small>
    <h3> the counter is: {{counter}}</h3>
     <button  v-on:click="doOperation(5)">Increment/Decrement</button>
     <hr>
     <small>>>>>>>example native event object</small>
     <br>
     <input type="text" v-on:input='setName'>
     <p>Your name : {{ name }} </p>\
     <hr>
     <small>Example of event modifiers</small>
     <form v-on:submit.prevent="submitForm">
       <input type="text">  <button> call me</button>
     </form>
     <button @click.right="alertMe">Only Right click works</button>

     <hr>
     <small>Counter with v-one </small>
      <h3 v-once> the counter is (with v-once): {{counter}}</h3>

      <hr>
      <small> v-bind:value can be written as :value   ||    v-on:click="methodName"  can be written as @click="methodName"</small>
    <hr>
    <small> VUE DYNAMIC STYLING</small>
    <!-- <div @click="boxSelected('A')" :style="{backgroundColor:boxASelected ? 'red' : 'gray'}" class="demo">AAA</div>
    <div @click="boxSelected('B')" :style="{backgroundColor:boxBSelected ? 'red' : 'gray'}"  class="demo">BBB</div>
    <div @click="boxSelected('C')" :style="{backgroundColor:boxCSelected ? 'red' : 'gray'}" class="demo">CCC</div> -->
     <div :class="{demo:true, active: boxASelected}" @click="boxSelected('A')">AAA</div>
    <div @click="boxSelected('B')"   class="demo">BBB</div>
    <div @click="boxSelected('C')"  class="demo">CCC</div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
 
   data() {
    return {
      htmlData: '<h1> hey ! I am hyper text written in data section</h1>',
      myLink:'https:google.co.in',
      counter:0,
      name:'',

      boxAselected:false,
       boxBselected:false,
        boxCselected:false,
    }
  },
  // this is now lloking for counter and when counter reches a special value , apply your logic, this is the
  //best use of wathers in vue
  watch:{
    counter(value){
      if(value==50){
        alert("its 50 now. controlled by watcher")
      }
    }
  },
  computed:{
       randomNumber(){
      return Math.random();
    },
  },
   methods: {
    // randomNumber(){
    //   return Math.random();
    // },
    executeMethod(){
      alert("Thank you for using event listner in vue")
    },
    doOperation(n){
      this.counter= this.counter+n;
    },
    setName(event){
      this.name= event.target.value;
    },
    submitForm(){
      alert("hi this is example of event modifiers")
    },
    alertMe(){
      alert("Haha:) You cant get this alert without right click. This is becoz of event modifiers. ")
    },

    boxSelected(box){
      if(box=='A'){
        this.boxAselected= true;
        alert(box)
      }
      if(box=='B'){
         alert(box)
        this.boxBselected= true;
      }
      if(box=='C'){
         alert(box)
        this.boxCselected= true;
      }
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
small{
  color: red;
  font-weight: bolder;
}
.demo{
  width: 200px;
  height: 200px;
  border: gray;
  display: inline-block;
  margin: 1rem;
}
.active{
     background: red;
}
</style>
