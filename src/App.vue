<script setup>

import  { ref, computed} from 'vue'

const favNum = ref([])

const counter = ref(0)

const increment = () => counter.value ++


const decrement = () => counter.value --


const reset = () => counter.value = 0

const classCounter = computed(()=> {

  if (counter.value === 0){
    return 'zero'
  }

  if(counter.value > 0){
    return 'green'
  }

  if(counter.value < 0){
    return 'red'
  }
}) 



const add = () => {
  favNum.value.push(counter.value)
  
}

const isRepeat = computed( () => {
  if(favNum.value.includes(counter.value)){
    return true
  }else {
    return false
  }

})

</script>






<template>
  <div class="container text-center mt-3">
    <div class="title text-center">
    <h1>Challenge  <i class="fa-regular fa-face-grin-squint fa-lg"></i></h1>
    </div>

    <h2 :class="classCounter"> {{ counter }}</h2>

    <div class="btn-group">
    <button @click="increment" class="btn btn-success" > increment </button>
    <button @click="decrement" class="btn btn-danger"> Decrement</button>
    <button @click="reset" class="btn btn-info"> Reset </button>
    <button @click="add" :disabled="isRepeat"    class="btn btn-light"> Add to fav </button>
  </div>
    <ul class="list-group mt-4">
      <li  class="list-group-item" v-for="(num, index) in favNum" :key="index"> 
        {{ num }}

      </li>
    </ul>
  </div>

</template>

<style scoped>

.green{
  color: green;
}

.red{
  color: red;
}

.zero{
  color: peru
}

.title{
  display: flex;
}


</style>