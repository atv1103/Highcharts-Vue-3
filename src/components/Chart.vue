<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount, watch } from "vue";
import Highcharts from "highcharts";

const props = defineProps<{
    chartArr: number[];
}>();

watch(
    () => props.chartArr,
  (newVal) => {
    dataRef.value = newVal; 
    if (chart) {
      chart.series[0].setData(dataRef.value);
    }
  },
  { deep: true }
);

const chartContainer = ref<HTMLElement | null>(null);
let chart: Highcharts.Chart | null = null;
const dataRef = ref([-6, -5, 0, 8, 15, 20, 22, 20, 14, 7, 0, -4]);

onMounted(() => {
  if (chartContainer.value) {
    //@ts-ignore
    chart = Highcharts.chart(chartContainer.value, {
      chart: {
        type: "line",
        width: 600,
        height: 300,
      },
      title: {
        text: "",
      },
      legend: {
        enabled: false,
      },
      xAxis: {
        labels: {
          enabled: false,
        },
        tickWidth: 10,
      },
      yAxis: {
        title: {
          text: "",
        },
        labels: {
          enabled: false,
        },
        gridLineWidth: 0,
        lineWidth: 1,
        tickWidth: 10,
      },
      series: [
        {
          name: "",
          data: dataRef.value,
          color: "#28a745",
        },
      ],
    });
  }
});

onBeforeUnmount(() => {
  if (chart) {
    chart.destroy();
  }
});
</script>

<template>
    <div ref="chartContainer" class="chart-container"></div>
  </template>

<style scoped>
.chart-container {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
