<script setup>
import { computed } from 'vue';

const props = defineProps(['champion']);
console.log(props.champion);

const splash = computed(() => {
    return `https://ddragon.leagueoflegends.com/cdn/img/champion/splash/${props.champion.name}_0.jpg`;
});
</script>

<template>
    <pre> {{ champion }}</pre>
    <img :src="splash" alt="champ_img">
    <h2> {{ props.champion.name }}</h2>
    <h3> "{{ props.champion.title }}"</h3>
    <div v-for="tag in props.champion.tags"> {{ tag }} </div>
</template>

<style scoped>

</style>
