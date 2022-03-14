<template>
  <div class="about">
    <h1>About Us</h1>
    <p></p>
      <br>
      <h1>Our Passion</h1>
  </div>
</template>

<script>
  export default {

  }
</script>

<style lang="scss" scoped>
$textcolor: white;

*{
  color: $textcolor;
}
  .about {
    padding-top: 125px;
    text-align: center;

    p {
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