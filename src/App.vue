<script>
import HeaderF from './components/HeaderF.vue';
import IntroSection from './components/IntroSection.vue';

export default {
  components: {
    HeaderF,
    IntroSection
  }
}
</script>

<template>
  <HeaderF />

  <main>
    <IntroSection />
  </main>
</template>

<style>
@import './assets/base.css';
</style>
