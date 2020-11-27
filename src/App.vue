<template>
  <div id="app">
    <v-app>
      <Header></Header>
      <HeroVideo></HeroVideo>
      <ThreeCol></ThreeCol>
      <SurveyAppDemo></SurveyAppDemo>
      <MovingTruck></MovingTruck>
      <SurveyAppDemo3></SurveyAppDemo3>
    </v-app>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import HeroVideo from './components/HeroVideo.vue'
import ThreeCol from './components/ThreeCol.vue'
import SurveyAppDemo from './components/SurveyAppDemo.vue'
import SurveyAppDemo3 from './components/SurveyAppDemo3.vue'
import MovingTruck from './components/MovingTruck.vue'

export default {
  name: 'App',
  components: {
    // SurveyAppDemo,
    // SurveyAppDemo2,
    Header,
    HeroVideo,
    ThreeCol,
    SurveyAppDemo,
    SurveyAppDemo3,
    MovingTruck
  }
}
</script>

<style>
  * {
    padding: 0;
    margin: 0;
  }
  .tempSpace {
    height: 1000px;
  }
</style>
