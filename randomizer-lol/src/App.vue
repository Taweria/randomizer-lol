<script setup>
import {ref} from 'vue';
import Card from '@/components/Card.vue';

const champions = ref([]);
const randomChamp = ref(null);

const getRandomChamp = async () => {
    const response = fetch('https://ddragon.leagueoflegends.com/cdn/13.24.1/data/en_US/champion.json')
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
    <Card v-if="randomChamp != null" :champion="randomChamp" />
    <button @click="getRandomChamp"> Random </button>
</template>

<style scoped>

</style>