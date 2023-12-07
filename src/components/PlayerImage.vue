<script setup>
const props = defineProps(["url"]);
</script>

<template>
  <div class="player-image__container">
    <img class="player-image" :src="props.url" alt="Player portrait" />
  </div>
</template>

<style>
.player-image__container {
  border-radius: 50%;
  border: 5px solid #fff;
  height: 120px;
  margin-left: 1rem;
  overflow: hidden;
  position: absolute;
  top: 9rem;
  width: 120px;
}

.player-image {
  height: 100%;
  width: 100%;
}
</style>
