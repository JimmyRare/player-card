<script setup>
import { ref, reactive, onMounted, watch } from "vue";
import PlayerImage from "./PlayerImage.vue";
import BodyData from "./BodyData.vue";
import Pie from "./Pie.vue";
import Rating from "./Rating.vue";

const props = defineProps(["player"]);
const {
  name,
  team,
  imageUrl,
  height,
  weight,
  year,
  passing,
  shooting,
  dribbling,
  rating,
  season,
} = props.player;
</script>

<template>
  <div class="card">
    <h1 class="card-title">{{ name }}</h1>
    <h2 class="card-team">{{ team }}</h2>
    <div class="card-bg__container">
      <img
        class="card-bg__image"
        src="../assets/bg-image.jpg"
        alt="Background image"
      />
    </div>
    <PlayerImage :url="imageUrl" />
    <BodyData :height="height" :weight="weight" :year="year" />
    <hr />
    <div class="card-pies">
      <Pie :percentage="passing" :border="8" :title="'Passa'"></Pie>
      <Pie :percentage="shooting" :border="8" :title="'Skjuta'"></Pie>
      <Pie :percentage="dribbling" :border="8" :title="'Dribbla'"></Pie>
    </div>
    <div class="card-season">
      <div class="card-season__year">Säsong {{ season[0].year }}</div>
      <hr />
      <ul class="card-season__stats">
        <li>{{ season[0].matches }} matcher</li>
        <li>{{ season[0].goals }} mål</li>
        <li>{{ season[0].assists }} assist</li>
      </ul>
      <hr />
      <div class="card-bottom">
        <Rating :rating="rating" />
        <input type="button" value="Ändra" />
      </div>
    </div>
  </div>
</template>

<style>
.card {
  background-color: #fff;
  border-radius: 15px;
  box-shadow: 3px 5px 10px 0px rgba(0, 0, 0, 0.1);
  height: 600px;
  margin: 0 auto;
  max-width: 95%;
  overflow: hidden;
  position: relative;
  width: 450px;
}

.card-title,
.card-team {
  color: #fff;
  font-size: 2.25rem;
  font-weight: 300;
  left: 1rem;
  margin-bottom: 0;
  position: relative;
  text-shadow: 0px 2px 4px rgba(0, 0, 0, 0.25);
  z-index: 1;
}

.card-team {
  font-size: 1.5rem;
  margin-bottom: 6.2rem;
  margin-top: 0.5rem;
}

.card-bg__container {
  height: 180px;
  overflow: hidden;
  position: absolute;
  top: 0;
}

.card-bg__container img {
  filter: blur(3px) brightness(60%);
  transform: translate(-10%, -25%);
}

.card-pies {
  display: flex;
  justify-content: space-between;
  margin: 0 1rem;
}

.card hr {
  background-color: var(--gray-100);
  border: none;
  height: 1px;
}

.card-season__year {
  font-weight: 300;
  margin: 1.5rem 1rem 0.5rem 1rem;
  text-align: center;
}

.card-season__stats {
  display: flex;
  justify-content: space-between;
  list-style: none;
  margin: 0 1rem;
  padding: 0;
}

.card-bottom {
  align-items: center;
  display: flex;
  justify-content: space-between;
  margin: 0 1rem;
}

input[type="button"] {
  background-color: var(--secondary);
  border: none;
  border-radius: 50px;
  color: #fff;
  cursor: pointer;
  font-size: 2rem;
  font-weight: 300 !important;
  height: 60px;
  padding: 0 1.5rem;
}
</style>
