<template>
  <div class="header">
    <div class="big">Показатель</div>
    <div class="success">Текущий день</div>
    <div>Вчера</div>
    <div>Этот день недели</div>
    <div class="big">Выручка, руб</div>
    <div class="success">500521</div>
    <div class="table__percent success">
        <span>480521</span>
        <span>4%</span>
    </div>
    <div class="failed">4805121</div>
  </div>
</template>

<style>
.header {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 5px;
}

.header > div {
  background-color: #eee;
  padding: 5px;
}

.big {
  grid-column: 1/3;
}

.table__percent {
  display: flex;
  justify-content: space-between;
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
