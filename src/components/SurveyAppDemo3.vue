<template>
<div>
  <div class="animWrapper">
    <div class="phoneContainer" >
      <img class="phone" src="../assets/ShyftX_hand.png" alt="phone" />
      <h4 v-if="visibleScrollMe">Please scroll</h4>
    </div>
    <transition name="fade">
      <div v-if="visibleChair" class="chairData overlayData" >
        <div class="overlayDataTitle">Chair</div>
        <div class="overlayDataInfo">
          <p>Total weight: 55.0</p>
          <p>Dimensions: 32” x 40” x 30</p>
          <p>Units: 1</p>
        </div>
      </div>
    </transition>
    <transition name="fade">
      <div v-if="visibleTv" class="tvData overlayData">
        <div class="overlayDataTitle">TV</div>
        <div class="overlayDataInfo">
          <p>Total weight: 55.0</p>
          <p>Dimensions: 32” x 40” x 30</p>
          <p>Units: 1</p>
        </div>
      </div>
    </transition>
    <transition name="fade">
      <div v-if="visibleSofa" class="sofaData overlayData">
        <div class="overlayDataTitle">Sofa</div>
        <div class="overlayDataInfo">
          <p>Total weight: 55.0</p>
          <p>Dimensions: 32” x 40” x 30</p>
          <p>Units: 1</p>
        </div>
      </div>
    </transition>
  </div>
  
  <!-- <div class="phoneAnimWrapper">
    <img class="phoneAnimImg" src="../assets/mobile-mockup-01.png" alt="">
  </div> -->
  <div class="space">

  </div>

</div>
</template>

<script>
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";

export default {
  name: 'SurveyAppDemo3',
  data: function () {
    return {
      visibleScrollMe: true,
      visibleChair: false,
      visibleTv: false,
      visibleSofa: false,
    }
  },
  methods: {
    toggleChair() {
      this.visibleChair = !this.visibleChair 
      console.log('toggle Chair')
    },
    toggleSofa() {
      this.visibleSofa = !this.visibleSofa 
    },
    toggleTv() {
      this.visibleTv = !this.visibleTv 
    },
    toggleScrollMe() {
      this.visibleScrollMe = !this.visibleScrollMe
    },

  },
  computed: {

  },
  mounted() {

    gsap.registerPlugin(ScrollTrigger);

    let tl = gsap.timeline({
      scrollTrigger: {
        trigger: ".animWrapper",
        scrub: true,
        pin: ".animWrapper",
        start: "top top",
        // end: "bottom bottom",
        markers: true,
      }
    })

    tl.to('.phoneContainer', {
      x: "33vw", 
      callbackScope: this,
      delay: 1,
      onStart: () => { this.toggleScrollMe() },
      onComplete: () => { this.toggleChair() },
      // onReverseComplete: () => { this.showScrollMe = true }
      })
      .to('.phoneContainer', {
      x: "56vw", 
      delay: 1,
      onStart: () => { this.toggleChair() },
      onComplete: () => { this.toggleSofa() },
      // onReverseComplete: () => { this.showChair = true }
      })
      .to('.phoneContainer', {
      x: "3vw", 
      delay: 1,
      onStart: () => { this.toggleSofa() },
      onComplete: () => { this.toggleTv() },
      // onReverseComplete: () => { this.showSofa = true }
    })

  }
}
</script>

<style scoped>
  .animWrapper {
    position: relative;
    background: url('../assets/ShyftX_room.jpg') no-repeat left center;
    -webkit-background-size: cover;
    -moz-background-size: cover;
    -o-background-size: cover;
    background-size: cover;
    width: 100vw;
    max-width:100%;
    height: 30vw;
    animation: slide 60s linear infinite;
  }
  .phoneContainer {
    position: absolute;
    bottom: 0;
    left: 3vw;
  }
   .phone {
    width: 67vw;
    vertical-align: bottom;
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
    height: 1500px;
  }
  .phoneAnimImg {
    width: 30vw;
  }
    .chairData {
    position: absolute;
    top: 12vw;
    left: 46vw;
  }
  .tvData {
    position: absolute;
    top: 10vw;
    left: 16vw;
  }
  .sofaData {
    position: absolute;
    top: 11vw;
    left: 65vw;
  }
  .overlayData {
    transition: all 0.5s ease-in-out;
  }
  .overlayDataTitle {
    width: 63px;
    height: 23px;
    background: #4C82BF;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.35);
    border-radius: 10px 10px 0 0;
    color: #fff;
    font-size: 14px;
    padding: 2px 0 0 6px;
  }
  .overlayDataInfo {
    width: 168px;
    height: 64px;
    background: #FFFFFF;
    border-radius: 0 10px 10px 10px;
    font-size: 12px;
    line-height: 127.5%;
    padding: 10px 6px 6px 6px;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.4);
  }
  .overlayDataInfo p {
    font-size: 12px;
    line-height: 1.2;
    margin: 0;
  }
  .fade-enter-active, .fade-leave-active {
    transition: opacity .3s;
  }
  .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
    opacity: 0;
  }
</style>