<template>
  <div id="app">
    <survey-app-demo></survey-app-demo>
    <survey-app-demo2></survey-app-demo2>
  </div>
</template>

<script>
import SurveyAppDemo from './components/SurveyAppDemo.vue'
import SurveyAppDemo2 from './components/SurveyAppDemo2.vue'

export default {
  name: 'App',
  components: {
    SurveyAppDemo,
    SurveyAppDemo2
  }
}
</script>

<style>
  * {
    padding: 0;
    margin: 0;
  }
</style>
