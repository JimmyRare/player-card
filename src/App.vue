<script setup>
import { ref, reactive, onMounted } from "vue";
import axios from "axios";

import Card from "./components/Card.vue";

const apiUrl = `${import.meta.env.VITE_API_URL}/PlayerData`;
console.log(apiUrl, import.meta.env);

let playerData = ref(null);

onMounted(async () => {
  playerData.value = await fetchPlayerData();
  console.log(playerData);
});

async function fetchPlayerData() {
  try {
    const response = await axios.get(apiUrl);
    return response.data;
  } catch (error) {
    console.error("Error fetching player data", error);
  }
}
</script>

<template>
  <Card v-if="playerData" :player="playerData" />
</template>

<style>
#app {
  background: linear-gradient(
    141deg,
    #d2d88d 7.23%,
    rgba(14, 116, 148, 0.67) 92.06%
  );
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  min-width: 100vw;
}
</style>
