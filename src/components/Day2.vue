<template>
<!-- This is Day 2 -->
  <div class="">
      <input v-model='enteredGoal' class="form-control" type="text">
      <button @click="addGoal" class="btn-primary btn">Add Goal</button>

    <p v-if="goals.length===0">No Goal Added For Now</p>

    <ul v-else>
        <li :key="goal" v-for="(goal,i) in goals" @click="removeGoal(i)">  <sup>{{i }}</sup> {{ goal }}   </li>
    </ul>
    <!-- v-for can be used to iterate through Objects -->
    <!-- v-for="(value,key,index) in ObjectName" -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      goals:[],
      enteredGoal:''
    }
  },
  methods: {
    addGoal(){
        this.goals.push(this.enteredGoal)
        console.log(this.goals);
    },
    removeGoal(index){
        this.goals.splice(index,1)
    }
  },
};
</script>

<style scoped>
input{
  font-size: 1.3rem;
  background: rgb(233, 229, 229);
  border-radius: 5px;
  font-weight: bolder;
}
button{
  font-size: 1.4rem;
  background: green;
  color: white;
   border-radius: 5px;
 
}
ul li{
  list-style: none;
  width: 400px;
  font-size: 1.8rem;
  background: yellowgreen;
  color: black;
  margin: .6rem auto;
  padding: .7rem;
  border-radius: 1rem;
  font-weight: bolder;
  box-shadow: 2px 4px 8px black;
  overflow: hidden;
}
p{
  color: red;
  font-size: 3rem;
  font-weight: 700;
}
</style>
