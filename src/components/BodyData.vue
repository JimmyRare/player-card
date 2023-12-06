<script setup>
import { ref } from "vue";
import { Icon } from "@iconify/vue";

const height = ref(185);
const weight = ref(85);
const year = ref(1982);
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
  justify-content: flex-end;
  list-style: none;
}

.body-data li {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 0 1.5rem;
}

.body-icon {
  height: 40px;
  margin-bottom: 0.5rem;
  opacity: 0.25;
  width: 40px;
}
</style>
