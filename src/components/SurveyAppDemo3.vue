<template>
<div>
  <div class="animContainer">
    <div class="animWrapper">
      <div class="phoneContainer" >
        <img class="phone" src="../assets/ShyftX_hand.png" alt="phone" />
        <h4 v-if="showScrollMe">Please scroll</h4>
      </div>
      <transition name="fade">
        <div v-show="showChair" class="chairData overlayData" >
          <div class="overlayDataTitle">Chair</div>
          <div class="overlayDataInfo">
            <p>Total weight: 55.0</p>
            <p>Dimensions: 32” x 40” x 30</p>
            <p>Units: 1</p>
          </div>
        </div>
      </transition>
      <transition name="fade">
        <div v-if="showTV" class="tvData overlayData">
          <div class="overlayDataTitle">TV</div>
          <div class="overlayDataInfo">
            <p>Total weight: 55.0</p>
            <p>Dimensions: 32” x 40” x 30</p>
            <p>Units: 1</p>
          </div>
        </div>
      </transition>
      <transition name="fade">
        <div v-if="showSofa" class="sofaData overlayData">
          <div class="overlayDataTitle">Sofa</div>
          <div class="overlayDataInfo">
            <p>Total weight: 55.0</p>
            <p>Dimensions: 32” x 40” x 30</p>
            <p>Units: 1</p>
          </div>
        </div>
      </transition>
    </div>
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
      showScrollMe: true,
      showChair: false,
      showTV: false,
      showSofa: false,
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
        pin: ".animContainer",
        // markers: true,
        start: "top top",
      }
    })

    t1.to('.phoneContainer', {
      x: "33vw", 
      // y: "5vw",
      duration: 4,
      onStart: () => { this.showScrollMe = false },
      onComplete: () => { this.showChair = true },
      onReverseComplete: () => { this.showScrollMe = true },
      delay: 2
      })
      .to('.phoneContainer', {
      x: "56vw", 
      // y: "-5vw",
      duration: 4,
      onStart: () => { this.showChair = false },
      onComplete: () => { this.showSofa = true },
      onReverseComplete: () => { this.showChair = true },
      delay: 2
      })
      .to('.phoneContainer', {
      x: "4vw", 
      // y: "-14vw",
      duration: 6,
      onStart: () => { this.showSofa = false },
      onComplete: () => { this.showTv = true },
      onReverseComplete: () => { this.showSofa = true },
      delay: 2
    })

    // gsap.to('.phoneAnimImg', {
    //   scrollTrigger: '.phoneAnimImg',
    //   duration: 2, 
    //   rotationY:-180, 
    //   repeat:-1, 
    //   yoyo:true, 
    //   stagger: 0.1
    // })
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
    left: 12vw;
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
    height: 1000px;
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