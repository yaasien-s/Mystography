<template>
  <div class="about">
    <h1>About Us</h1>
    <br>
    <div class="row">
      <div class="col-sm-6">
    <h3>Head of MYS'Tography</h3>
    <p>Muhammad Yaasien Salaam is the Head of MYS'Tography where he oversees all functions of the business including
      engineering and operations. A designer at heart, Yaasien is known for balancing sharp design thinking with
      thoughtful product strategy to create experiences that bring people together and encourage authentic
      communication.

      Born and raised in Cape Town, South Africa, he still lives in Cape Town with his family.</p>
      </div>
      <div class="col-sm-6">
    <h3 class="founder">Founders</h3>
    <p>Yaasien Salaam founded MYS'Tography and serves as CEO for 8 years now, he pursues his next passion project. With Dale De Kock focus on simplicity and inspiring creativity through solving
      problems with thoughtful product design, MYS'Tography became the home for innovation on visual aesthetics launching
      dozens of photographers including showcasing and live chats.</p>
      </div>
    </div>
    <br>

    <!-- Carousel -->
  </div>
</template>

<script>
  export default {

  }
</script>

<style lang="scss" scoped>
  $textcolor: white;
  $mobilecolor: black;

  * {
    color: $textcolor;

    @media (max-width: 780px) {
      color: $mobilecolor;
    }
  }

  .about {
    padding-top: 125px;
    text-align: center;

    @media (max-width: 780px) {
      padding-top: 100px;
      padding-bottom: 75px;
    }

    .row {
      margin-inline: auto;
    }
    p {
      width: 75%;
      margin-inline: auto;
      margin-top: 30px;
      text-align: initial;

      @media (max-width: 780px) {
        width: 75%;
        text-align: center;
      }

    }
      @media (max-width: 575px) {
        .founder{
          margin-top: 50px !important;
        }
      }
  }
</style>