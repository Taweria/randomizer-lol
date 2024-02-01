<script setup>
import {ref} from 'vue';
import Card from '@/components/Card.vue';

const champions = ref([]);
const randomChamp = ref(null);

const getRandomChamp = async () => {
    const response = fetch('https://ddragon.leagueoflegends.com/cdn/14.2.1/data/en_US/champion.json')
        .then(response => response.json())
        
    const data = await response;
    champions.value = Object.values(data.data);
    randomChamp.value = champions.value[getRandomInt(champions.value.length)];
    // console.log(randomChamp.value);
}

const getRandomInt = (max) => {
    return Math.floor(Math.random() * max);
}
</script>

<template>
    <div class="div-button"><button @click="getRandomChamp"> Random </button></div>
    <Card v-if="randomChamp != null" :champion="randomChamp" />
</template>

<style>
body{
    background-color: #252525;
}
.div-button{
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 25px 0;

}
button {
  font-family: 'Marcellus SC', serif;
  font-size: 30px;
  font-weight: bold;
  letter-spacing: 1px;
  padding: 5px 15px; 
  background: #1e2328;
  color: #cdbe91;
  box-shadow: inset 0 0 2px #000000;
  border-image: linear-gradient(to bottom, #c8aa6d, #7a5c29);
  border-image-slice: 1;
  border-width: 2px;
}

button:hover {
  text-shadow: 0 0 5px #ffffff80;
  box-shadow: 0 0 8px 0 #ffffff50;
  background: linear-gradient(to bottom, #1e2328, #433d2b);
  cursor: pointer;
  transition: 0.1s;
}

button:active {
  text-shadow: none;
  box-shadow: none;
  color: #cdbe9130;
}
</style>