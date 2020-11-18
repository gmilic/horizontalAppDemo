<template>
    <v-app-bar
      absolute
      color="rgba(18, 33, 32, 0.64)"
      elevate-on-scroll
      scroll-target="#scrolling-techniques-7"
    >
      <v-img
        class="mx-2"
        src="../assets/ShyftX_logo.svg"
        max-height="40"
        max-width="160"
        contain
      ></v-img>

      <v-spacer></v-spacer>

      <v-toolbar-items class="hidden-xs-only">
        <v-btn
          to="/"
          color="transparent"
          dark
          flat
          elevation="0"
        >
        What we do
        </v-btn>
                <v-btn
          to="/"
          color="transparent"
          dark
          flat
          elevation="0"
        >
        How it works
        </v-btn>        <v-btn
          to="/"
          color="transparent"
          dark
          flat
          elevation="0"
        >
        Pricing
        </v-btn>        <v-btn
          to="/"
          color="transparent"
          dark
          flat
          elevation="0"
        >
        Resources
        </v-btn>
      </v-toolbar-items>


        <v-btn
          class="mx-4"
          to="/"
          outlined
          color="#fff"
        >
          Log in
        </v-btn>
        <v-btn
          class="mx-4"
          to="/"
          color="#4A81C1"
          dark
        >
          Get A Free Demo
        </v-btn>


      <v-app-bar-nav-icon></v-app-bar-nav-icon>
    </v-app-bar>
</template>

<script>
export default {
  name: 'Header'

}
</script>

<style>

</style>