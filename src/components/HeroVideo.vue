<template>
    <div class="hero">
    <video playsinline autoplay muted loop poster='/assets/truck_forest.jpg'>
      <source :src='require("@/assets/truck_forest_720.mp4")' type='video/mp4'>
    </video>
    <div class="heroText">
      <h2 class="text-h5 heroTextH2 heroTextH201 text-md-h2 font-weight-bold my-4">Full Trucks.</h2>
      <h2 class="text-h5 heroTextH2 heroTextH202 text-md-h2 font-weight-bold my-4">No off-seasons.</h2>
      <h2 class="text-h5 heroTextH2 heroTextH203 text-md-h2 font-weight-bold my-4">Contactless video surveys.</h2>
      <h5 class="heroText-subtitle">Market leader in tools for technology for moving companies to provide estimates, collect payments and get leads.</h5>
      <v-btn
        depressed
        color="#4A81C1"
        class="my-6 heroTextBtn"
        dark
      >
        Sign up
      </v-btn>
    </div>
  </div>
</template>

<script>
import { gsap } from "gsap";

export default {
  name: 'HeroVideo',
    mounted: function() {
      
      // function text01() {
      //   let tl = gsap.timeline();
      //   tl.from('.heroText01', {
      //     // x: "+=100", 
      //     // y: "+=100",
      //     // rotate: "20",
      //     rotateX: 90,
      //     opacity: 0,
      //     duration: 3,
      //     delay: 1
      //   })
      //   return tl;
      // }

      // function text02() {
      //   let tl = gsap.timeline();
      //   tl.from('.heroText02', {
      //     // x: "+=100", 
      //     // y: "+=100",
      //     // rotate: "20",
      //     rotateX: 0,
      //     opacity: 0,
      //     duration: 3,
      //     delay: 1
      //   })
      //   return tl;
      // }

      // function text03() {
      //   let tl = gsap.timeline();
      //   tl.from('.heroText03', {
      //     // x: "+=100", 
      //     // y: "+=100",
      //     // rotate: "20",
      //     rotateX: 0,
      //     opacity: 0,
      //     duration: 3,
      //     delay: 1
      //   })
      //   return tl;
      // }

      // var master = gsap.timeline();
      // master.add(text01())
      //   .add(text02(), "+=2")     //with a gap of 2 seconds
      //   .add(text03(), "-=1") //overlap by 1 second

      let tl = gsap.timeline({repeat: -1})

      tl
      .from('.heroTextH201', {
        rotationX: 90,
        duration: .3,
        ease: "power2.out",
        // delay: .1
      })
      .to('.heroTextH201', {
        rotationX: 90,
        duration: .3,
        ease: "power2.out",
        opacity: 0,
        delay: 3
      })
      .from('.heroTextH202', {
        rotationX: 90,
        duration: .3,
        ease: "power2.out",
        // delay: .1
      })
      .to('.heroTextH202', {
        rotationX: 90,
        duration: .3,
        ease: "power2.out",
        opacity: 0,
        delay: 3
      })
      .from('.heroTextH203', {
        rotationX: 90,
        duration: .3,
        ease: "power2.out",
        // delay: .1
      })
      .to('.heroTextH203', {
        rotationX: 90,
        duration: .3,
        ease: "power2.out",
        opacity: 0,
        delay: 3
      })

    }
}
</script>

<style scoped>
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
    top: 50%;
    transform: translateY(-50%);
    /* left: 0;
    right: 0;
    margin: auto; */
    left: 10vw;
    max-width: 450px;
    color: #fff;
  }
  .heroTextH203 {
    position: absolute;
    top: -150px;
    left: 0;
  }
  .heroTextH202,
  .heroTextH201 {
    position: absolute;
    top: -90px;
    left: 0;
  }
  .heroText-subtitle {
    font-size: 1em;
    line-height: 1.2;
    font-weight: 400;
  }
</style>