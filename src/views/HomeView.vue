<script setup>
import { ref } from 'vue';


let character = ref([])

async function loadCharacters(){
  const response = await fetch(`http://rickandmortyapi.com/api/character?page=1`)
  const data = await response.json()
  character.value = date.results
  console.log(data)
}

loadCharacters()


</script>

<template>
 <div class="flex justify-center mt-10">
  <h1 class="text-5xl">Personajes de Rick & Morty</h1>
 </div>

 <div v-for="personaje in character" :key="character.id"></div>

<!--<Card character="character"/>-->
</template>
