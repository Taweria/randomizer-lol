<script setup>
import { computed } from 'vue';

const props = defineProps(['champion']);

const splash = computed(() => {
    const cleanedChampionName = props.champion.name.replace(/\s+/g, '').replace(/'/g, '').replace(/\./g, '');
    return `https://ddragon.leagueoflegends.com/cdn/img/champion/splash/${cleanedChampionName}_0.jpg`;
});

</script>

<template>
    <!-- <pre> {{ champion }}</pre> -->
    <img :src="splash" alt="champ_img">
    <h2> {{ props.champion.name }}</h2>
    <h3> "{{ props.champion.title }}"</h3>
    <div class="div-tags">
        <div v-for="tag in props.champion.tags" class="tags"> {{ tag }} </div>
    </div>
</template>

<style scoped>
img{
    display: block;
    margin: 0 auto;
    width: 100%;
    max-width: 800px;
    border-radius: 10px;
}
h2{
    color: #fff;
    font-size: 2rem;
    font-weight: 400;
    margin: 0 auto;
    text-align: center;
    text-transform: uppercase;
    /* text-shadow: 0 0 10px #e3df67; */
}
h3{
    color: #fff;
    font-size: 25px;
    font-weight: 400;
    margin: 15px 0;
    text-align: center;
    text-transform: uppercase;
    text-decoration: underline;
    text-underline-offset: 10px;

}
.div-tags{
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 25px 0;
}
.tags{
    font-family: 'Marcellus SC', serif;
    font-size: 25px;
    font-weight: bold;
    letter-spacing: 1px;
    padding: 5px 15px; 
    background: #1e2328;
    color: #cdbe91;
    box-shadow: inset 0 0 2px #000000;
    border-image: linear-gradient(to bottom, #c8aa6d, #7a5c29);
    border-image-slice: 1;
    border-width: 2px;
    margin: 0 5px;
}
</style>
