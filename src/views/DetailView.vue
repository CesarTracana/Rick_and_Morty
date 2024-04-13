<template>
  <div v-if="character" class="about">

    <div class="grid grid-cols-2">
      <div class="m-12">
        <img class="h-full w-full rounded-3xl":src= character.image alt="">
      </div>
      <div class="flex flex-col items-center justify-center m-12 space-y-8">
        <div class="flex justify-center">
         <h1 class="text-5xl font-bold">{{ character.name }}</h1>
        </div>
        <p class="text-2xl font-bold">Genero: {{ character.gender }}</p>
         <br>
         <p class="text-2xl font-bold">Especie: {{ character.species }}</p>
         <br>
         <p class="text-2xl font-bold">Estado: {{ character.status }}</p>
         <br>
         <p class="text-2xl font-bold">Creacion: {{ character.created }}</p>
         <br>
         <p class="text-2xl font-bold">Origen: {{ character.origin.name }}</p>
         <br>
         <p class="text-2xl font-bold">Locacion: {{ character.location.name }}</p>
       
      </div>
    </div>
  </div>
</template>

<script setup> 
 import { useRoute} from 'vue-router';
 import {onMounted, ref} from "vue"
 const character = ref(null)

 const route = useRoute()
 const characterId = route.params.id
 onMounted(async() => {
 try{
  const response = await fetch(`https://rickandmortyapi.com/api/character/${characterId}`)
  const data = await response.json()
  character.value = data
  console.log(data)
 }
 catch{


 }


 })
</script>
