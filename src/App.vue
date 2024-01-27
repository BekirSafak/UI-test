<script setup lang="ts">
import Card from "./components/Card.vue";
import Progress from "./components/Progress.vue";
import CircularProgress from "./components/Circural.vue";
import ResponseCard from "./components/ResponseCard.vue";
import Dialog from "./components/Dialog.vue"


</script>

<template>
  <div class="center">
    <Card></Card>
    <ResponseCard></ResponseCard>
    <Dialog></Dialog>
    <Progress></Progress>
    <CircularProgress :progress="75" :size="150" :strokeWidth="12" />
  </div>
</template>

<style lang="scss">
@import './assets/style.scss';
</style>
