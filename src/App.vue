<template>
  <div id="app">
    <v-app>
      <Header></Header>
      <SurveyAppDemo3></SurveyAppDemo3>
    </v-app>
  </div>
</template>

<script>
// import SurveyAppDemo from './components/SurveyAppDemo.vue'
// import SurveyAppDemo2 from './components/SurveyAppDemo2.vue'
import SurveyAppDemo3 from './components/SurveyAppDemo3.vue'
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    // SurveyAppDemo,
    // SurveyAppDemo2,
    SurveyAppDemo3,
    Header
  }
}
</script>

<style>
  * {
    padding: 0;
    margin: 0;
  }
</style>
