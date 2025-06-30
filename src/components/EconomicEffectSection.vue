<template>
  <section class="economic-effect-section">
    <h2>
      Экономический эффект от внедрения<br />
      ERP-системы с ГЭНДАЛЬФ:
    </h2>
    <div class="donut-charts-row">
      <AnimatedDonutChart v-for="(item, idx) in data" :key="idx" :percent="item.percent" :label="item.label"
        :delay="idx * 500" />
    </div>
  </section>
</template>

<script setup>
/* eslint-env vue/setup-compiler-macros */
import AnimatedDonutChart from './AnimatedDonutChart.vue'

const data = [
  { percent: 32, label: "Трудозатраты в различных подразделениях" },
  { percent: 30, label: "Объемы материальных запасов" },
  { percent: 10, label: "Расходы на материальные ресурсы" },
  { percent: 10, label: "Операционные и административные расходы" },
  { percent: 5, label: "Себестоимость продукции/услуг" },
]
</script>

<style scoped>
.economic-effect-section {
  text-align: center;
  background: linear-gradient(161deg, #EFF7FF -7.51%, #6ED5EE 56.83%), linear-gradient(322.4deg, #4C0091 11.93%, #00FFE1 95.31%);
}

.donut-charts-row {
  display: flex;
  width: 100%;
  justify-content: space-between;
  padding: 50px 0;
}

h2 {
  font-weight: 600;
  font-size: 48px;
  text-align: center;
  background: linear-gradient(182.38deg, #0E98BA -12.81%, #021B44 96.99%), #E6F2FF;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  text-fill-color: transparent;
}
</style>