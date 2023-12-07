<script setup>
import { ref } from "vue";
import { Icon } from "@iconify/vue";

const { height, weight, year } = defineProps(["height", "weight", "year"]);
</script>

<template>
  <ul class="body-data">
    <li><Icon icon="ion:man" class="body-icon" />{{ height }} cm</li>
    <li>
      <Icon icon="material-symbols:weight-sharp" class="body-icon" />
      {{ weight }} kg
    </li>
    <li><Icon icon="bi:calendar" class="body-icon" /> {{ year }}</li>
  </ul>
</template>

<style>
.body-data {
  display: flex;
  justify-content: space-between;
  list-style: none;
  margin: 0 1rem 0 calc(120px + 2rem);
  padding: 0;
}

.body-data li {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.body-icon {
  height: 40px;
  margin-bottom: 0.5rem;
  opacity: 0.25;
  width: 40px;
}
</style>
