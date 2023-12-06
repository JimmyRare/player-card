<script setup>
const props = defineProps({
  border: Number,
  percentage: Number,
  title: String,
});
</script>

<template>
  <div>
    <div class="pie__title">{{ title }}</div>
    <div class="pie pie--animate">{{ percentage }}</div>
  </div>
</template>

<style>
@property --percentage {
  syntax: "<number>";
  inherits: true;
  initial-value: 0;
}

@keyframes percentage {
  from {
    --percentage: 0;
  }
}

.pie--animate {
  animation: percentage 1s 0.5s both;
}

.pie__title {
  font-size: 1.5rem;
  font-weight: 100;
  margin-bottom: 0.5rem;
  text-align: center;
}
.pie {
  --percentage: v-bind(percentage);
  aspect-ratio: 1;
  border-radius: 50%;
  display: inline-grid;
  font-size: 40px;
  font-weight: bold;
  height: 80px;
  overflow: hidden;
  place-content: center;
  position: relative;
  transform-style: preserve-3d;
  width: 80px;
}

.pie:before {
  background: conic-gradient(
    var(--primary) calc(var(--percentage) * 1%),
    #0000 0
  );
  background-color: rgba(243, 204, 21, 0.25);
  border-radius: 50%;
  content: "";
  inset: 0;
  height: 80px;
  mask: radial-gradient(
    farthest-side,
    #0000 calc(100% - v-bind(border + "px")),
    #000 calc(100% - v-bind(border + "px"))
  );
  -webkit-mask: radial-gradient(
    farthest-side,
    #0000 calc(100% - v-bind(border + "px")),
    #000 calc(100% - v-bind(border + "px"))
  );
  position: absolute;
  transform: translateZ(10px);
  width: 80px;
}
</style>
