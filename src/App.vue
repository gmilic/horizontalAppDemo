<template>
  <div id="app">
    <v-app>
      <Header></Header>
      <HeroVideo></HeroVideo>
      <ThreeCol></ThreeCol>
      <SurveyAppDemo3></SurveyAppDemo3>
    </v-app>
  </div>
</template>

<script>
// import SurveyAppDemo from './components/SurveyAppDemo.vue'
// import SurveyAppDemo2 from './components/SurveyAppDemo2.vue'
import Header from './components/Header.vue'
import HeroVideo from './components/HeroVideo.vue'
import ThreeCol from './components/ThreeCol.vue'
import SurveyAppDemo3 from './components/SurveyAppDemo3.vue'

export default {
  name: 'App',
  components: {
    // SurveyAppDemo,
    // SurveyAppDemo2,
    Header,
    HeroVideo,
    ThreeCol,
    SurveyAppDemo3,
  }
}
</script>

<style>
  * {
    padding: 0;
    margin: 0;
  }
</style>
