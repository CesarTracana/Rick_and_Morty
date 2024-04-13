<script setup>
import { ref } from 'vue';
import card  from "../components/Card.vue";

let character = ref([]);
let page = ref(1)

function nextPage(){
  page.value++
  loadCharacters()
}

function previousPage(){
  page.value--
  if(page.value<1){
    page.value=1
  }
  loadCharacters()
}

async function loadCharacters(){
  const response = await fetch(`https://rickandmortyapi.com/api/character?page=${page.value}`);
  const data = await response.json();
  character.value = data.results;
  console.log(data);
}

loadCharacters();


</script>

<template>
 <div class="flex justify-center mt-10">
  <h1 class="text-5xl text-rose-950">Personajes de Rick & Morty</h1>
 </div>

 <div class="flex justify-center items-center m-4 space-x-4">
 <button class="bg-gray-300 rounded-xl text-center p-4"@click="previousPage" :disabled="page===1">Pagina anterior</button>
 <div>{{ page }}</div>
 <button  class="bg-gray-300 rounded-xl text-center p-4"@click="nextPage">Siguiente pagina</button>
 </div>

 <div class="grid gap-4 grid-cols-4 m-6">
<router-link v-for="personaje in character" :key="character.id" :to="`/${personaje.id}`">
  <card :character="personaje"></card>
</router-link>
</div>

 <br><br>

 <!--<Card character="character"/>-->
</template>
