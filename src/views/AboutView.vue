<template>
  <div class="about">
    <h1>About Us</h1>
    <br>
    <div class="row">
      <div class="col-sm-6">
        <img src="@/assets/images/about-img.jpg" alt="">
      </div>
      <br>
      <div class="col-sm-6">
        <h3>Head of MYS'Tography</h3>
        <p>Muhammad Yaasien Salaam is the Head of MYS'Tography where he oversees all functions of the business including
          engineering and operations. A designer at heart, Yaasien is known for balancing sharp design thinking with
          thoughtful product strategy to create experiences that bring people together and encourage authentic
          communication.

          Born and raised in Cape Town, South Africa, he still lives in Cape Town with his family.</p>
        <!-- <br> -->
        <p>Yaasien Salaam founded MYS'Tography and serves as CEO for 2 years now, he pursues his next passion project.
          With Dale De Kock focus on simplicity and inspiring creativity through solving
          problems with thoughtful product design, MYS'Tography became the home for innovation on visual aesthetics
          launching
          dozens of photographers including showcasing and live chats.</p>
      </div>
    </div>
    <button @click="back" id="Back">Go Back</button>
    <!-- Carousel -->
  </div>
</template>

<script>
  export default {
    methods: {
       back() {
    this.$router.go(-1)
        },
    }
  }
</script>

<style lang="scss" scoped>
  $textcolor: white;
  $mobilecolor: black;

  * {
    color: $mobilecolor;

    @media (max-width: 780px) {
      color: $mobilecolor;
    }
  }

  .about {
    padding-top: 125px;
    text-align: center;
    padding-bottom: 70px;

    @media (max-width: 780px) {
      padding-top: 100px;
      padding-bottom: 75px;
    }

    .row {
      margin-inline: auto;

      .col-sm-6 {

        img {
          width: 75%;
          height: 84.7%;
          overflow: hidden;
          object-position: top;
          object-fit: cover;

          @media (max-width: 575px) {
            padding-bottom: 50px !important;
          }
        }
      }

    }

    p {
      width: 75%;
      margin-inline: auto;
      margin-top: 30px;
      text-align: initial;

      @media (max-width: 780px) {
        width: 75%;
        text-align: initial;
      }

    }

    button {
      position: fixed;
      right: 30px;
      bottom: 100px;
       margin: 30px auto;
            margin-bottom: 0;
            width: 10%;
            font-weight: 600;
            padding: 5px;
            border: none;
            background: rgba($color: #ffffff, $alpha: .8);
            transition: .5s ease all;

            &:hover {
                background: rgba($color: #000000, $alpha: .8);
                transition: .5s ease all;
                color: #ffffff;
            }

            @media (max-width: 768px) {
                width: 35%;
            }
    }
  }
</style>