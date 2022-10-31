<template>
  <v-layout class="mt-5">
    <v-main>
      <div class="financial-component">
        <div class="financial-wrapper">
          <div class="financial-left">
            <p class="financial-title">
              Access financial reports and stock market forecasts easier than ever
            </p>
            <p class="financial-title">
              Get the results of hundreads of hours of research. Condensed and accessible through your account.
            </p>
            <v-img
              :lazy-src="require('@/assets/images/Financial.jpg?lqip')"
              max-height="500"
              max-width="650"
              :src="require('@/assets/images/Financial.jpg?webp')"
            />
            <p class="financial-title">
              Don't waste time. Trade Smarter.
            </p>
          </div>
          <div class="financial-right">
            <v-img
              class="right-image"
              :lazy-src="require('@/assets/images/Business-Guy.jpg?webp')"
              max-height="auto"
              max-width="650"
              :src="require('@/assets/images/Business-Guy.jpg?webp')"
            />
          </div>
          <v-btn
            class="white--text get-started-button"
            color="#6018dc"
            depressed
            rounded
            large
          >
            Get started
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
      .get-started-button {
          width: 200px;
      }
      .financial-wrapper {
          width: 80%;
          margin-left: auto;
          margin-right: auto;
          display: flex;
          font-family: Arial, Helvetica, sans-serif;
      }
      .financial-left {
          display: flex;
          flex-direction: column;
          justify-content: space-between;
          margin-bottom: 6rem;
      }
      .financial-title {
          color: #6018dc;
          font-weight: 600;
          word-spacing: 2px;
          letter-spacing: 2px;
      }
  @media only screen and (max-width: 700px) {
      .financial-wrapper {
          flex-direction: column;
      }
      .financial-left p {
          width: 92%;
          margin-left: auto;
          margin-right: auto;
          text-align: center;
          margin-top: 10px;
      }
      .get-started-button {
          width: 80vw;
          margin-top: 2rem;
      }
      .financial-right {
        margin-top: -5rem;;
      }
  }
  @media only screen and (min-width: 700px) {
      .financial-wrapper {
          position: relative;
      }
      .get-started-button {
          position: absolute;
          bottom: 10px;
          left: 0;
      }
  }
  </style>
