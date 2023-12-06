<script setup>
import { Icon } from "@iconify/vue";

const props = defineProps({
  rating: Number,
});
</script>

<template>
  <div class="rating">
    Betyg:
    <ul class="rating-symbols">
      <li v-for="(_, i) in rating" :key="i">
        <Icon icon="material-symbols:star" :height="24" class="rating-icon" />
      </li>
    </ul>
  </div>
</template>

<style>
.rating {
  align-items: center;
  display: flex;
  font-weight: 700;
  margin: 1rem;
}

.rating-symbols {
  display: flex;
  list-style: none;
  margin-left: 0.5rem;
  margin-top: 1rem;
  padding: 0;
}

.rating-icon {
  color: var(--primary);
}
</style>
