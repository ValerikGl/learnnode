<script setup>
import axios from 'axios';
import { ref } from 'vue';
import CharacterCard from '../components/CharacterCard.vue';
let characters = ref([]);
let info = ref({});
getCharacters('https://rickandmortyapi.com/api/character');


function getCharacters(url){
    axios.get(url).then(response => {
    console.log(response);
    characters.value = response.data.results;
    info.value = response.data.info;
});
}
function next(){
    getCharacters(info.value.next);
}

function prev(){
    getCharacters(info.value.prev);
}
</script>
<template>
<div class="container">
    <button class="button is-primary" @click="prev" :disabled="!info.prev">Prev</button>
    <button class="button is-primary" @click="next" :disabled="!info.next">Next</button>
    <div class="columns is-multiline">
        <div class="column is-one-quarter" v-for="character in characters">
            <CharacterCard :character="character"></CharacterCard>
        </div>
    </div>
    
</div>
</template>