<script setup>
import {ref, computed} from 'vue'
  const name = 'Vue dinámico'
 const arrayFrutas = [{name: 'manzana', price: "$1,00", description: "UNA MANZANA", stock: 0},{name: 'pera', price: "$21,00", description: "UNA pera", stock: 10},{name: 'banana', price: "$2,00", description: "UNA banana", stock: 2},{name: 'kiwi', price: "$11,00", description: "UNA kiwi", stock: 22},{name: 'naranja', price: "$41,00", description: "UNA naranja", stock: 33}]
 const objetoFruta={name: 'manzana', price: "$1,00", description: "UNA MANZANA"}


//metodo - methods
// const handleClick = (message) =>{
//   console.log(message)
//}

const list = ref([])
const counter = ref(0);
const decrement = () => {
  counter.value --;
}
const reset = () => {
  counter.value = 0;
}
const increment =()=>{
  counter.value ++;
  console.log(counter)
}
const addfav = ()=>{
  list.value.push(counter.value)
  console.log(list)
}
const classDisFav = computed(()=>{
  if (list.value.includes(counter.value)) {
    return true
  }
  else {
    return false
  }
})
//computed si o si un return
const classCounter = computed(()=>{
  if (counter.value === 0) {
    return 'zero'
  }
  if(counter.value > 0){
    return 'mayorcero'
  }
  if(counter.value < 0){
    return 'menorcero'
  }
})

</script>

<template>

  <h1>Hola {{ name.toUpperCase() }}</h1>
  <!-- <h2>{{ arrayColores }}</h2>
  <h2 :style="`color: ${arrayColores[0]}`">Hola {{ name }}</h2>
  <h2>{{ activo ? 'Estoy activo' : 'Estoy inactivo' }}</h2>f="activo === true">Estoy activo</h2> -->
  <!-- <ul>
    <template  v-for="item in arrayFrutas"
      :key="item.name">
      <li
      v-if="item.stock > 0"
     >
       {{ item.name }} - {{ item.price }}
     </li>
    </template>
  </ul>
  <button v-on:click.right.prevent="handleClick('texsto right')">Activame right</button>
  <button @click="handleClick('texto left')">Activame left</button>
  <button @click.middle="handleClick('texto middle')">Activame middle</button> -->
 
  <h2 :class="classCounter">{{ counter }}</h2>

  <button @click="increment">
    Aumentar
  </button>
  <button @click="decrement">
    Restar
  </button>
  <button @click="reset">
    Resetear
  </button>
  <button :disabled="classDisFav" @click="addfav">
    Add FAv
  </button>
  <ul>
    <template  v-for="item in list"
      :key="item">
    <li>
      {{ item }}
    </li>
    </template>
  </ul>
</template>


<style>
h1{
  color: red;
}
.menorcero{
  color: red;
}
.mayorcero{
  color: green;
}
.zero{
  color: peru
}
</style>