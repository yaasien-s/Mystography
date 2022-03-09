<template>
  <div class="about">
    <h1 class="text-light">About Us</h1>
    <p>We at MYS'Tography, we as in royal we, loves interacting with poeple, animals, nature. Always believing that
      evrything and everyone has their own type of beauty. I'd like to show the world how I see everything in it's
      nartural state of beauty.</p>
      <br>
      <h1 class="text-light">Our Passion</h1>
  </div>
</template>

<script>
  export default {

  }
</script>

<style lang="scss" scoped>
  .about {
    padding-top: 100px;
    text-align: center;

    p {
      color: #fff;
      width: 50%;
      margin-inline: auto;
      margin-top: 30px;
      text-align: initial;

      @media (max-width: 780px) {
        width: 75%;
        text-align: center;
      }
    }
  }
</style>