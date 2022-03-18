<template>
  <NavBar />
  <Footer />
</template>
<script>
  import Footer from '@/components/Footer.vue'
  import NavBar from '@/components/NavBar.vue'
  export default {
    components: {
      NavBar,
      Footer
    },
  };
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Noto+Serif+Display:ital,wght@1,300&family=Poppins:wght@200&display=swap');

  * {
    font-family: 'Noto Serif Display', serif;
    font-family: 'Poppins', sans-serif;
  }

  body {
    // background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url("@/assets/images/backgroundmap.jpg");
    // background-position: center;
    // background-size: cover;
    // background-attachment: fixed;
    // background-repeat: no-repeat;
    // height: 100vh;
    // z-index: -100;

    @media (max-width: 780px) {
      background-image: none;
    }
  }
</style>