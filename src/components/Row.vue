<script setup lang="ts">
import { computed } from "vue";

const props = defineProps<{
  item: {
    id: string;
    name: string;
    current_day: number;
    yesterday: number;
    that_day: number;
    chartInfo: number[];
  };
}>();

const { item } = props;

const emit = defineEmits<{
  (event: "item-click", chartInfo: number[]): void;
}>();

const percent = computed(() => {
  return Math.round(
    ((item.current_day - item.yesterday) / item.current_day) * 100
  );
});

const percentClass = computed(() => {
  console.log(percent.value);
  return percent.value > 0 ? "success" : percent.value < 0 ? "failed" : "";
});

const handleClick = () => {
  emit("item-click", item.chartInfo);
};
</script>

<template>
  <div class="table" @click="handleClick">
    <div class="table__name">{{ item.name }}</div>
    <div :class="percentClass">{{ item.current_day }}</div>
    <div :class="percentClass" class="table__percent">
      <span>{{ item.yesterday }}</span>
      <span>{{ percent }}%</span>
    </div>
    <div :class="percentClass">{{ item.that_day }}</div>
  </div>
</template>

<style>
.table {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 5px;
  margin: 5px 0;
  cursor: pointer;
}

.table > div {
  background-color: #eee;
  padding: 5px;
}

.table__name {
  grid-column: 1/3;
}

.table__percent {
  display: flex;
  justify-content: space-between;
}

.table__percent span {
  width: 49%;
}

div.success {
  background-color: rgba(40, 167, 69, 0.4);
}

div.success > span:last-child {
  color: green;
}

div.failed {
  background-color: rgba(247, 42, 42, 0.4);
}

div.failed > span:last-child {
  color: red;
}
</style>
