<script setup>
import { ref, reactive, onMounted, watch } from "vue";
import axios from "axios";

import Card from "./components/Card.vue";

const apiUrl = `${import.meta.env.VITE_API_URL}/PlayerData`;

const state = reactive({
  playerData: null,
});

onMounted(async () => {
  await fetchPlayerData();
});

async function fetchPlayerData() {
  try {
    const response = await axios.get(apiUrl);
    state.playerData = response.data;
  } catch (error) {
    console.error("Error fetching player data", error);
  }
}
</script>

<template>
  <Card
    v-if="state.playerData"
    @generate="fetchPlayerData"
    :player="state.playerData"
  />
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
