<script setup lang="ts">
import Header from "./components/Header.vue";
import Chart from "./components/Chart.vue";
import Table from "./components/Table.vue";
import { ref } from "vue";

const chartArr = ref<number[]>([0]) 

const handleItemClick = (chartInfo: number[]) => {
  chartArr.value = chartInfo
};

</script>

<template>
  <div id="app">
    <h1>График с использованием Highcharts и Vue 3</h1>
    <Header />
    <Chart :chartArr="chartArr" />
    <Table @item-click="handleItemClick" />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  align-items: center;
}
</style>
