<template>
  <v-app>
    <v-img
      class="image-content"
      :lazy-src="require('@/assets/images/Hero-Image.jpg?lqip')"
      max-height="auto"
      max-width="100vw"
      :src="require('@/assets/images/Hero-Image.jpg?webp')"
    />
    <div class="form-title">
      <h1>Analyst Ratings</h1>
      <h5>Every trader's best friend.</h5>
    </div>
    <v-btn
      class="white--text find-out"
      color="#6018dc"
      depressed
      rounded
      large
    >
      Find out more <v-icon>mdi-chevron-down</v-icon>
    </v-btn>
  </v-app>
</template>

<script>
export default {

}
</script>

  <style>
      .image {
          position: relative;
      }
      .form-title {
          position: absolute;
          top: 10vh;
          left: 10vw;
      }
      .form-content {
          position: absolute;
          top: 10vh;
          right: 7vw;
      }
      .form-title > h1 {
          color: #6018dc;
          text-transform: uppercase;
          letter-spacing: 2px;
          font-family: 'Playfair Display', serif;
          font-style: italic;
          font-weight: 500;
          font-size: 50px;
      }
      .form-title > h5 {
          font-family: Arial, Helvetica, sans-serif;
          word-spacing: 1px;
          font-size: 20px;
          margin-top: 10px;
      }
      @media only screen and (max-width: 700px) {
          .form-title {
              margin-top: -10%;
              text-align: center;
          }
          .find-out {
              width: 90vw;
              margin-left: auto;
              margin-right: auto;
          }
          .form-title > h1 {
            font-size: 2.5rem;
          }
      }
      @media only screen and (min-width: 700px) {
          .find-out {
              display: none;
          }
      }
      @media only screen and (max-width: 870px) {
          .form-title > h1 {
            margin-top: 3rem;
            font-size: 3rem;
          }
      }
  </style>
