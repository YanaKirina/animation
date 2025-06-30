<template>
  <section>
    <h2>Зачем вам автоматизировать предприятие на базе систем ERP?</h2>
    <div class="container-top">
      <div class="container-top-img">
        <img src="@/assets/hand.png" alt="" class="hand">
        <div class="gear-wrapper">
          <img ref="gear1" src="@/assets/gears/gear1.png" class="gear" style="top: 50px; left: 40px"
            @mouseenter="startRotation(0)" @mouseleave="stopRotation(0)" />
          <img ref="gear2" src="@/assets/gears/gear2.png" class="gear" style="top: 20px; left: 250px"
            @mouseenter="startRotation(1)" @mouseleave="stopRotation(1)" />
          <img ref="gear3" src="@/assets/gears/gear3.png" class="gear" style="top: 140px; left: 400px"
            @mouseenter="startRotation(2)" @mouseleave="stopRotation(2)" />
        </div>
      </div>
      <div class="container-top-description">
        <p>ERP-система — это не просто инструмент для управления бизнесом, а ваш ключ к масштабированию и
          эффективной работе компании. Она автоматизирует и интегрирует критически важные процессы, такие как
          производство, продажи, бухгалтерия, логистика и управление персоналом. Ваша команда получает доступ
          к актуальной информации в реальном времени, что устраняет барьеры между отделами и исключает ошибки.
          В результате, бизнес работает как единое целое, где каждый процесс предсказуем и управляем.</p>
        <p>Интеграция критически важных процессов — от производства и бухгалтерии до логистики и HR — даёт
          доступ к актуальной информации, исключает ошибки и объединяет все отделы в единую экосистему. Вы
          сокращаете затраты, ускоряете процессы и повышаете прозрачность управления. Система помогает
          прогнозировать и предотвращать проблемы, обеспечивая конкурентное преимущество и гибкость перед
          любыми изменениями рынка.</p>
      </div>
    </div>
    <h3>Почему стоит сделать выбор в пользу ERP-систем от «1С»</h3>
    <div class="carousel-container">
      <button ref="prevEl" class="arrow left">
        <img src="@/assets/arrow.png" class="rotated" alt="←" />
      </button>

      <Swiper :modules="[Navigation]" :slides-per-view="3" :space-between="20" :navigation="{
        prevEl: prevEl,
        nextEl: nextEl
      }" class="swiper">
        <SwiperSlide v-for="(slide, index) in slides" :key="index">
          <div class="slide">
            <img :src="slide.icon" class="slide-floating-icon" />
            <p v-html="slide.title" />
            <p>{{ slide.text }}</p>
          </div>
        </SwiperSlide>
      </Swiper>
      <button ref="nextEl" class="arrow right">
        <img src="@/assets/arrow.png" alt="→" />
      </button>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import { gsap } from 'gsap'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Navigation } from 'swiper/modules'
import 'swiper/css'
import 'swiper/css/navigation'

const gear1 = ref(null)
const gear2 = ref(null)
const gear3 = ref(null)
const gearRefs = [gear1, gear2, gear3]

const timelines = []

function startRotation(index) {
  const gear = gearRefs[index].value
  if (!gear) return

  const currentRotation = gsap.getProperty(gear, 'rotation') || 0

  if (timelines[index]) timelines[index].kill()

  timelines[index] = gsap.to(gear, {
    rotation: currentRotation + 360,
    duration: 2 + index,
    repeat: -1,
    ease: 'linear',
    transformOrigin: '50% 50%'
  })
}

function stopRotation(index) {
  const tl = timelines[index]
  if (tl) {
    tl.kill()
    timelines[index] = null
  }
}


const prevEl = ref(null)
const nextEl = ref(null)


const slides = [
  {
    icon: require('@/assets/carousel/4.png'),
    title: 'Повышение эффективности.',
    text: '1С:ERP улучшает рабочие процессы и помогает принимать решения на основе актуальных данных',
  },
  {
    icon: require('@/assets/carousel/5.png'),
    title: 'Поддержание конкурентоспособности.',
    text: 'Автоматизация становится ключевым фактором для удержания позиций на динамичном рынке.',
  },
  {
    icon: require('@/assets/carousel/6.png'),
    title: 'Управление из любой точки мира.',
    text: '1C:ERP позволяет контролировать все процессы через облако и мобильные устройства (iOS, Android, Windows), с постоянными обновлениями и поддержкой электронной отчетности.',
  },
  {
    icon: require('@/assets/carousel/7.png'),
    title: 'Идеально для любой отрасли.',
    text: 'ERP-системы «1С» подходятдля агропрома, строительства, машиностроения и других сфер, а также легко интегрируется с любым оборудованием и программами.',
  },
  {
    icon: require('@/assets/carousel/8.png'),
    title: 'Поддержка популярных операционных систем и баз данных.',
    text: 'ERP от «1С» работает на ОС Linux, Windows, Mac OS, PostgreSQL и других, адаптируясь под ваши процессы.',
  },
  {
    icon: require('@/assets/carousel/9.png'),
    title: 'Надежная защита данных.',
    text: 'Система обеспечивает строгий контроль доступа к информации, сертифицирована ФСТЭК, гарантируя безопасность ваших данных.',
  }
]

</script>

<style scoped>
section {
  background: linear-gradient(0deg, #00728C 0%, #005F82 11.11%, #004C77 22.22%, #003969 33.33%, #002659 44.44%, #001C4C 55.56%, #001944 66.67%, #001334 100%);
  position: relative;
}

h2 {
  font-weight: 600;
  font-size: 48px;
  padding: 0 5vw;
  text-align: center;
  background: linear-gradient(137.41deg, #EFF7FF 0.5%, #6ED5EE 59.79%), #E6F2FF;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  text-fill-color: transparent;
}

.container-top {
  display: flex;
  font-family: 'Open Sans';
  font-style: normal;
  font-weight: 400;
}

.container-top div {
  width: 50%;
}

.container-top-description {
  padding: 25px;
}

.container-top-description p:first-child {
  font-size: 20px;
  line-height: 27px;
  color: #E6F2FF;
  padding: 48px 0;
}

.container-top-description p:last-child {
  font-size: 16px;
  line-height: 22px;
  color: #021B44;
  background: linear-gradient(137.41deg, #EFF7FF 0.5%, #6ED5EE 59.79%), linear-gradient(137.41deg, #0F6FD4 0.5%, #011438 59.79%), #D9D9D9;
  box-shadow: 0px 0px 24px 10px rgba(192, 222, 255, 0.4);
  border-radius: 5px;
  padding: 32px;
}

h3 {
  text-align: center;
  background: linear-gradient(137.41deg, #EFF7FF 0.5%, #6ED5EE 59.79%), #E6F2FF;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  text-fill-color: transparent;
}

.hand {
  position: absolute;
  left: 0;
  top: 30%;
}

.gear-wrapper {
  position: relative;
  width: 100%;
  height: 400px;
}

.gear {
  position: absolute;
  cursor: pointer;
  user-select: none;
}

.carousel-container {
  position: relative;
  width: 100%;
  padding: 20px 0px;
}

.swiper-wrapper {
  overflow: hidden;
}

.slide {
  margin-top: 60px;
  height: 300px;
  display: flex;
  flex-direction: column;
  background: linear-gradient(180deg, rgba(0, 114, 140, 0.4) 0%, rgba(0, 29, 80, 0.4) 58%, rgba(0, 16, 44, 0.4) 100%);
  border-radius: 5px;
  padding: 104px 24px 24px 24px;
  cursor: url('@/assets/hand-cursor.svg'), auto;
  position: relative;
}


.slide-floating-icon {
  position: absolute;
  top: -30px;
  left: 24px;
  height: 120px;
  z-index: 2;
  pointer-events: none;
  filter: drop-shadow(0 4px 24px rgba(0,0,0,0.18));
}

.slide p:first-of-type{
  color: #E6F2FF;
  font-size: 20px;
  font-weight: 700;
}

.slide p:last-of-type{
  color: #E6F2FF;
  font-size: 16px;
  font-weight: 400;
  padding-top: 8px;
}

.arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: none;
  border: none;
  cursor: pointer;
  z-index: 10;
}

.arrow.left {
  left: -50px;
}

.arrow.right {
  right: -50px;
}

.arrow img {
  width: 32px;
}

.rotated {
  transform: rotate(180deg);
}
</style>




