<template>
  <v-layout>
    <v-img
      class="mobile"
      :lazy-src="require('@/assets/images/Footer-Mobile.jpg?lqip')"
      height="auto"
      max-width="100vw"
      :src="require('@/assets/images/Footer-Mobile.jpg?webp')"
    />
    <v-img
      class="desktop"
      :lazy-src="require('@/assets/images/Footer.jpg?lqip')"
      height="auto"
      max-width="100vw"
      :src="require('@/assets/images/Footer.jpg?webp')"
    />
  </v-layout>
</template>

<script>
export default {
}
</script>

  <style>
  .desktop, .mobile {
    display: none;
  }
  @media only screen and (max-width: 700px) {
    .mobile {display: block;}
  }
  @media only screen and (min-width: 701px) {
    .desktop {display: block;}
  }
  </style>
