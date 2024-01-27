<template>
    <div class="circular-progress">
        <svg :width="size" :height="size" class="progress-ring">
            <circle :cx="radius" :cy="radius" :r="radius - strokeWidth / 2" fill="transparent" :stroke="trackColor"
                :stroke-width="strokeWidth"></circle>
            <circle :cx="radius" :cy="radius" :r="radius - strokeWidth / 2" fill="transparent" :stroke="progressColor"
                :stroke-width="strokeWidth" :stroke-dasharray="circumference" :stroke-dashoffset="dashoffset"></circle>
        </svg>
    </div>
</template>
  
<script setup>
import { ref, onMounted, watch } from 'vue';

const progress = ref(25);
const size = ref(100);
const strokeWidth = ref(10);
const trackColor = ref('#f8f2fd');
const progressColor = ref('#8c60a8');
const radius = ref(size.value / 2);
const circumference = ref(2 * Math.PI * radius.value);
const dashoffset = ref(0);

onMounted(() => {
    watch(() => progress.value, updateProgress);
    watch(() => size.value, updateSize);
    watch(() => radius.value, updateCircumference);

    updateCircumference();
    updateProgress();
});

function updateSize() {
    radius.value = size.value / 2;
    circumference.value = 2 * Math.PI * radius.value;
    updateProgress();
}

function updateCircumference() {
    circumference.value = 2 * Math.PI * radius.value;
    updateProgress();
}

function updateProgress() {
    dashoffset.value = circumference.value * (1 - progress.value / 100);
}
</script>
  
<style lang="scss">
@import '../assets/circural/circural.scss'
</style>