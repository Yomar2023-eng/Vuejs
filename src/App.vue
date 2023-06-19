<script setup>

import { ref,computed } from "vue";
const name = "Con Yomar Barrios";


const contador = ref(0);
const arrayfavoritos = ref([]);

const decrement = ()=>{
  
  contador.value--;
};
const increment = ()=>{
  
  contador.value++;
};

const reset =()=>{
  contador.value=0;
};
const add =()=>{
  arrayfavoritos.value.push(contador.value);
};

const blokearbtn = computed(()=>{
  const numsearch = arrayfavoritos.value.find((num)=>num===contador.value);
  console.log(numsearch);
  if(numsearch ===0){
    return true;

    
  }
  
  return numsearch ? true : false;
 
});



const contadocomputer = computed (()=>{
  if(contador.value===0){
  return 'zero'
   }
  if(contador.value > 0){
    return 'positivo'
  }
  if(contador.value < 0){
    return 'negativo'
  }


})



</script>




<template>
<div  class="container text-center ">
<h1>Aprendiendo Vue.js {{ name }}</h1>
<h2 :class="contadocomputer">{{ contador }}</h2>
<div class=" btn-group">
<button @click="decrement" class="btn btn-success ">Restar</button>
<button @click="increment" class="btn btn-info ">Aumentar</button>
<button @click="reset" class="btn btn-danger">Reset</button>
<button @click="add" :disabled="blokearbtn " class="btn btn-secondary " >Guardar</button>
</div>
<!--{{ arrayfavoritos }} -->
<br>
<br>
<ul class="list-group list-group-flush">
  <li 
  v-for="(num, index) in arrayfavoritos"
  :key="num">{{ num }}</li>
</ul>
</div>
</template>

<style>

.list-group{
  color: yellowgreen;
}

li{
  color: blueviolet;
}
h1 {
  color: blue;
}

h2 {
  color: blue;
}

.positivo{
  color: blueviolet;

}
.negativo{
  color: brown;
}
.zero{
  color: white;
}

</style>