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

<style>

body{
    background-image: url("@/assets/images/backgroundmap.jpg");
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    height: 100vh;
}
</style>