<template>
<div>
  <div class="animWrapper">
    <div class="phoneContainer" >
      <img class="phone" src="../assets/telefon02.png" alt="phone" />
      <h4 v-if="showDragMe">{{ objectType }}</h4>
      <div v-if="showObjectName" class="showChairWrapp">{{ objectType }}</div>
    </div>
  </div>
  <div class="space">

  </div>
  <div class="space1"></div>
</div>
</template>

<script>
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";

export default {
  name: 'AppDemo2',
  data: function () {
    return {
      showDragMe: true,
      showObjectName: false,
      objectType: "Please Scroll"
    }
  },
  methods: {

  },
  computed: {

  },
  mounted: function() {

    gsap.registerPlugin(ScrollTrigger);

    let t1 = gsap.timeline({
      scrollTrigger: {
        trigger: ".animWrapper",
        scrub: 1,
        pin: ".animWrapper",
        markers: true,
        start: "top top",
      }
    })

    t1.to('.phoneContainer', {
      x: "53vw", 
      y: "5vw",
      duration: 2,
      onStart: () => { this.objectType = "" },
      onComplete: () => { this.objectType = "chair" },
      onReverseComplete: () => { this.objectType = "Please scroll" },
      delay: 1
      })
      .to('.phoneContainer', {
      x: "28vw", 
      y: "-5vw",
      duration: 2,
      onStart: () => { this.objectType = "" },
      onComplete: () => { this.objectType = "plant" },
      onReverseComplete: () => { this.objectType = "chair" },
      delay: 2
      })
      .to('.phoneContainer', {
      x: "0vw", 
      y: "-14vw",
      duration: 2,
      onStart: () => { this.objectType = "" },
      onComplete: () => { this.objectType = "TV" },
      onReverseComplete: () => { this.objectType = "plant" },
      delay: 2
      })
  }
}
</script>

<style scoped>
  .animWrapper {
    overflow: hidden;
    position: relative;
    background: url('../assets/bg169.jpg') repeat-x center center;
    -webkit-background-size: cover;
    -moz-background-size: cover;
    -o-background-size: cover;
    background-size: cover;
    width: 100vw;
    max-width:100%;
    height: 56vw;
  }
  .phoneContainer {
    position: absolute;
    bottom: 0;
  }
  .phone {
    width: 55vw;
  }

  h4 {
    color: #eee;
    text-shadow: 2px 2px 6px #000;
    font-size: 2em;
    position: absolute;
    top: 39%;
    left: 16%;
    font-family: sans-serif;
  }
  .showChairWrapp {
    color: #eee;
    text-shadow: 2px 2px 6px #000;
    font-size: 2em;
    position: absolute;
    top: 39%;
    left: 16%;
    font-family: sans-serif;
  }
  .space, .space1 {
    height: 2000px;
  }
</style>