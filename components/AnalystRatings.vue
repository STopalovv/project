<template>
  <v-layout>
    <v-main>
      <div class="pa-10 purple">
        <div class="d-flex flex-column flex-md-row justify-space-between wrapper">
          <div class="ml-16 d-flex flex-column justify-space-between left">
            <p class="text-sm-body-2 font-weight-bold white--text text-md-p text-lg-h6">
              Analyst Ratings gives you stock intel by top-rated analysts who look deeply in the companies you want to know about.
            </p>
          </div>
          <div class="mr-16">
            <v-img
              class="left-image"
              :lazy-src="require('@/assets/images/Analysts.jpg?lqip')"
              max-height="350"
              max-width="650"
              :src="require('@/assets/images/Analysts.jpg?webp')"
            />
          </div>
          <v-btn
            class="purple--text font-weight-bolder align-self-stretch left-button"
            color="#ff526ce0"
            depressed
            rounded
            large
          >
            Let's go!
          </v-btn>
        </div>
      </div>
    </v-main>
  </v-layout>
</template>

<script>
export default {

}
</script>

  <style>
  .left-button {
      width: 20vw;
  }
     p {
      width: 45%;
      word-spacing: 1.5px;
      letter-spacing: 1.1px;
    }
     @media only screen and (max-width: 600px) {
    .left p {
      width: 80%;
      text-align: center;
      margin-top: 10px;
    }
    .left {
      position: relative;
    }
    .left-image {
      width: 120%;
    }
    .left-button {
      width: 100%;
      margin-top: 3rem;
      font-weight: 800;
      margin-left: auto;
      margin-right: auto;
    }
   }
  @media only screen and (min-width: 769px) {
    .wrapper {
      position: relative;
    }
    .left-button {
      position: absolute;
      bottom: 10px;
      left: 4.5%;
    }
  }
  </style>

  <!-- 320px — 480px: Mobile devices.
  481px — 768px: iPads, Tablets.
  769px — 1024px: Small screens, laptops.
  1025px — 1200px: Desktops, large screens.
  1201px and more — Extra large screens, TV. -->
