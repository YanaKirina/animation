<template>
  <MainHeader></MainHeader>
  <AppNavigation></AppNavigation>
  <InteractiveErpIntro></InteractiveErpIntro>
  <HaveQuestions></HaveQuestions>
  <EconomicEffectSection />
</template>

<script>
import MainHeader from './components/MainHeader.vue';
import AppNavigation from './components/AppNavigation.vue';
import InteractiveErpIntro from './components/InteractiveErpIntro.vue';
import HaveQuestions from './components/HaveQuestions.vue'
import EconomicEffectSection from './components/EconomicEffectSection.vue';

export default {
  name: 'App',
  components: {
    MainHeader,
    AppNavigation,
    InteractiveErpIntro,
    HaveQuestions,
    EconomicEffectSection
  }
}
</script>

<style>

</style>
