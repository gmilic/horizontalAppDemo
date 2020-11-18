<template>
<div>

  <div class="hero">
    <video playsinline autoplay muted loop poster='/assets/City-Traffic-1.jpg'>
      <source :src='require("@/assets/city-traffic-2.mp4")' type='video/mp4'>
    </video>
    <div class="heroText">
      <h2 class="text-h2 font-weight-bold">Full Trucks</h2>
      <h5 class="text-h5 font-weight-bold">ShyftX delivers smarter tools and expert support to run your moving company with confidence.</h5>
      <v-btn
        depressed
        color="primary"
        class="my-12"
      >
        Sign up
      </v-btn>
    </div>
  </div>
    <v-container class="grey lighten-5 mt-16">
      <v-row>
        <v-col
          cols="12"
          sm="4"
          >
          <h3>Lump sum shipments</h3> 
          <p>We've teamed up with RMCs and Corporations to give transferees a business class journey.</p>
        </v-col>
              <v-col
          cols="12"
          sm="4"
          >
          <h3>Lump sum shipments</h3> 
          <p>We've teamed up with RMCs and Corporations to give transferees a business class journey.</p>
        </v-col>
              <v-col
          cols="12"
          sm="4"
          >
          <h3>Lump sum shipments</h3> 
          <p>We've teamed up with RMCs and Corporations to give transferees a business class journey.</p>
        </v-col>
      </v-row>
    </v-container>

  <div class="animWrapper">
    <div class="phoneContainer" >
      <img class="phone" src="../assets/telefon02.png" alt="phone" />
      <h4 v-if="showDragMe">{{ objectType }}</h4>
      <div v-if="showObjectName" class="showChairWrapp">{{ objectType }}</div>
    </div>
  </div>
  <div class="phoneAnimWrapper">
    <img class="phoneAnimImg" src="../assets/mobile-mockup-01.png" alt="">
  </div>
  <div class="space">

  </div>

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
        scrub: 2,
        pin: ".animWrapper",
        // markers: true,
        start: "top top",
      }
    })

    t1.to('.phoneContainer', {
      x: "53vw", 
      y: "5vw",
      duration: 6,
      onStart: () => { this.objectType = "" },
      onComplete: () => { this.objectType = "chair" },
      onReverseComplete: () => { this.objectType = "Please scroll" },
      delay: 1
      })
      .to('.phoneContainer', {
      x: "28vw", 
      y: "-5vw",
      duration: 4,
      onStart: () => { this.objectType = "" },
      onComplete: () => { this.objectType = "plant" },
      onReverseComplete: () => { this.objectType = "chair" },
      delay: 2
      })
      .to('.phoneContainer', {
      x: "0vw", 
      y: "-14vw",
      duration: 4,
      onStart: () => { this.objectType = "" },
      onComplete: () => { this.objectType = "TV" },
      onReverseComplete: () => { this.objectType = "plant" },
      delay: 2
    })

    gsap.to('.phoneAnimImg', {
      scrollTrigger: '.phoneAnimImg',
      duration: 2, 
      rotationY:-180, 
      repeat:-1, 
      yoyo:true, 
      stagger: 0.1
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
    height: 1000px;
  }
  .hero {
    position: relative;
    width: 100vw;
    max-width: 100%;
    height: 56vw;
  }
  .hero video {
    width: 100%;
  }
  .heroText {
    position: absolute;
    top: 200px;
    left: 200px;
    color: #fff;
  }
</style>