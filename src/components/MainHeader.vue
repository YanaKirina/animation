<template>
  <section>
    <div class="header-left">
      <h1 class="title" :style="titleStyle" @mousemove="handleMouseMove">1С:ERP</h1>
      <p>Инновационные методы и инструменты для вашего бизнеса</p>
      <div class="rounded-button-background">
        <button>Заказать внедрение 1С:ERP</button>
      </div>
    </div>
    <div>
      <img src="@/assets/factory.png" alt="">
      <img src="@/assets/Sochetanie-3.png" alt="">
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      traX: 40,
      traY: 50
    }
  },
  computed: {
    titleStyle() {
      return {
        backgroundPosition: `${this.traX}% ${this.traY}%`
      }
    }
  },
  methods: {
    handleMouseMove(e) {
      const x = e.clientX / window.innerWidth;
      const y = e.clientY / window.innerHeight;

      this.traX = 100 + (x * 300 - 150);
      this.traY = 50 + (y * 300 - 150);

    }
  }
}
</script>

<style scoped>
section{
  background: linear-gradient(180deg, #00728C 0%, #005F82 11.11%, #004C77 22.22%, #003969 33.33%, #002659 44.44%, #001C4C 55.56%, #001944 66.67%, #001334 100%);
  display: flex;
  padding-top: 5%;
  height: 100vh;
  position: relative;
  overflow: hidden
}

.header-left {
  width: 60%;
  padding-right: 5vw;
}

.title {
  color: transparent;
  background-image: url("@/assets/back.jpg");
  background-size: 170%;
  background-position-x: center;
  -webkit-background-clip: text;
  background-clip: text;
  padding: 0px;

}

p {
  color: #E6F2FF;
  font-size: 40px;
  padding: 40px 0;
}


button {
  font-size: 24px;
  padding: 16px 40px;
  font-weight: 700;
  background: linear-gradient(137.41deg, #EFF7FF 0.5%, #6ED5EE 59.79%), linear-gradient(137.41deg, #EFF7FF 0.5%, #81C6FF 59.79%), linear-gradient(322.4deg, #4C0091 11.93%, #00FFE1 95.31%);
  box-shadow: 24.799px 28.528px 75.6px rgba(20, 24, 42, 0.233);
  border-radius: 5px;
  color: #011438;

}

.rounded-button-background{
  box-sizing: border-box;
    border-radius: 15px;
    padding: 10px;
    border: 1px solid rgba(255, 255, 255, 0.24);
    box-shadow: 0px 0px 8px 10px rgb(125, 127, 255);
    backdrop-filter: blur(12px);
    background: rgb(1, 20, 56);
    transition: all 0.4s ease;
    width: fit-content
}

img:last-child {
  padding-top: 70px;
}
img:first-child{
  position: absolute;
    bottom: 0;
    left: 35%;
}
</style>
