<template>
    <div class="progress-bar">
        <div class="progress" :style="{ width: `${progress}%` }"></div>
    </div>
</template>
  
<script setup lang="ts">
const progress = 50

</script>
  
<style lang="scss">
@import "../assets/progress/progress.scss"; // SCSS dosyanızın yolu buraya gelecek
</style>
  