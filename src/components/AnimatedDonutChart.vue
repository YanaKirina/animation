/* eslint-env vue/setup-compiler-macros */
<template>
  <div ref="container" class="donut-chart" :class="{ visible: isVisible }">
    <svg :width="size" :height="size">
      <defs>
        <linearGradient id="text-gradient" x1="0" y1="0" x2="0" y2="1">
          <stop offset="0%" stop-color="#0E98BA"/>
          <stop offset="100%" stop-color="#021B44"/>
        </linearGradient>
      </defs>
      <circle
        :stroke="baseColor"
        fill="none"
        :stroke-width="stroke"
        :cx="size/2"
        :cy="size/2"
        :r="radius"
      />
      <circle
        ref="progressCircle"
        :stroke="progressColor"
        fill="none"
        :stroke-width="stroke"
        :cx="size/2"
        :cy="size/2"
        :r="radius"
        :stroke-dasharray="circumference"
        :stroke-dashoffset="circumference"
        :transform="`rotate(-90 ${size/2} ${size/2})`"
        style="transition: stroke-dashoffset 0.5s linear"
      />
      <text
        x="50%"
        y="50%"
        text-anchor="middle"
        dy=".3em"
        font-size="45"
        font-weight="700"
        fill="url(#text-gradient)"
        style="line-height:60px;dominant-baseline:middle;"
      >
        -{{ percent }}%
      </text>
    </svg>
    <div class="donut-label">{{ label }}</div>
  </div>
</template>

<script setup>
import { ref, onMounted, watch } from 'vue'
import { gsap } from 'gsap'

const props = defineProps({
  percent: Number,
  label: String,
  delay: Number,
  size: { type: Number, default: 220 },
  stroke: { type: Number, default: 30 },
  baseColor: { type: String, default: '#021B44' },
  progressColor: { type: String, default: '#00FFC3' }
})

const isVisible = ref(false)
const container = ref(null)
const progressCircle = ref(null)

const radius = props.size / 2 - props.stroke / 2
const circumference = 2 * Math.PI * radius

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => {
      if (entry.isIntersecting) {
        isVisible.value = true
        observer.disconnect()
      }
    },
    { threshold: 0.5 }
  )
  if (container.value) observer.observe(container.value)
})

watch(isVisible, (val) => {
  if (val) {
    setTimeout(() => {
      gsap.to(progressCircle.value, {
        strokeDashoffset: circumference - (props.percent / 100) * circumference,
        duration: 1,
        ease: 'power2.out'
      })
    }, props.delay || 0)
  }
})
</script>

<style scoped>
.donut-chart {
  width: 25%;
  text-align: center;
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.5s, transform 0.5s;
}
.donut-chart.visible {
  opacity: 1;
  transform: translateY(0);
}
.donut-label {
  position: relative;
  width: 220px;
  height: 75px;
  margin: 0 auto;
  font-family: 'Wix Madefor Display', sans-serif;
  font-style: normal;
  font-weight: 700;
  font-size: 20px;
  line-height: 25px;
  text-align: center;
  color: #021B44;
  display: flex;
  align-items: center;
  justify-content: center;
  white-space: pre-line;
}
</style> 