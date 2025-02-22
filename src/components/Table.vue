<script setup lang="ts">
import Row from "./Row.vue";

const list = [
  {
    id: "1",
    name: "Наличный расчет",
    current_day: 300000,
    yesterday: 300000,
    that_day: 300000,
    chartInfo: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12],
  },
  {
    id: "2",
    name: "Безналичный расчет",
    current_day: 100000,
    yesterday: 100000,
    that_day: 300000,
    chartInfo: [1, 5, 8, 2, 6, 6, 11, 19, 20, 10, 8, 12],
  },
  {
    id: "3",
    name: "Кредитные карты",
    current_day: 100521,
    yesterday: 100521,
    that_day: 100521,
    chartInfo: [5, 2, 8, 5, 15, 9, 6, 6, 1, 2, 3, 6],
  },
  {
    id: "4",
    name: "Средний чек, руб",
    current_day: 1300,
    yesterday: 900,
    that_day: 900,
    chartInfo: [12, 11, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1],
  },
  {
    id: "5",
    name: "Количество чеков",
    current_day: 34,
    yesterday: 36,
    that_day: 34,
    chartInfo: [4, 1, 3, 10, 15, 16, 5, 13, 2, 22, 15, 12],
  },
];

const emit = defineEmits<{
  (event: 'item-click', chartInfo: number[]): void;
}>();

const handleItemClick = (chartInfo: number[]) => {
  emit('item-click', chartInfo);
};
</script>

<template>
  <Row
    v-for="item in list"
    :key="item.id"
    :item="item"
    @item-click="handleItemClick"
  />
</template>
