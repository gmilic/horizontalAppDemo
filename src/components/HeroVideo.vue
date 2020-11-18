<template>
    <div class="hero">
    <video playsinline autoplay muted loop poster='/assets/truck_forest.jpg'>
      <source :src='require("@/assets/truck_forest_720.mp4")' type='video/mp4'>
    </video>
    <div class="heroText">
      <h2 class="text-h5 text-md-h2 font-weight-bold my-4">Full Trucks</h2>
      <h5 class="text-h6 font-weight-bold">ShyftX delivers smarter tools and expert support to run your moving company with confidence.</h5>
      <v-btn
        depressed
        color="#4A81C1"
        class="my-6"
        dark
      >
        Sign up
      </v-btn>
    </div>
  </div>
</template>

<script>
export default {

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
    left: 15vw;
    max-width: 400px;
    color: #fff;
  }
</style>