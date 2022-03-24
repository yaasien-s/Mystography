<template>
  <div class="home">
    <div id="landing">
      <h1 class="text-light">Welcome <br> to <br> Myst</h1>
      <router-link :to="{name: 'About'}"><button>Learn More</button></router-link>
    </div>
    <h1>What we do?</h1>
    <br>
    <p class="w-75">At MYS'T we want to show everyone the beauty of photography, showcase the different type
      of styles in
      photography. We are all about bringing people together through photography, no matter where in the world.
      We want you to have direct communication with your favourite photographer, chat with them, speak about how they
      inspire you to become a photographer yourself. If you feeling for a collab or
      just to hire them for a shoot.
    </p>
    <br><br>
<div class="row">
  <div class="col-sm-3">
    <img src="@/assets/images/camera.jpg" alt="">
  </div>
  <div class="col-sm-3">
    <img src="@/assets/images/compass.jpg" alt="">
  </div>
  <div class="col-sm-3">
    <img src="@/assets/images/lion.jpg" alt="">
  </div>
  <div class="col-sm-3">
    <img src="@/assets/images/book.jpg" alt="">
  </div>
  <!-- <div class="col-sm-2">
    <img src="@/assets/images/ocean.jpg" alt="">
  </div> -->
</div>

<Contact/>
  </div>
</template>

<script>
import Contact from '../components/Contact.vue'
  // @ is an alias to /src
  export default {

    components: {
      Contact,
    }

  }
</script>
<style lang="scss" scoped>
  $primarytext: red;

  .home {
    padding-bottom: 100px;

    h1 {
      text-align: center;
      margin: 50px auto;
    }

    p {
      margin-inline: auto;
      text-align: center;

      @media (max-width: 780px) {
        text-align: initial !important;
      }
    }

    .row {
      width: 95%;
      margin-inline: auto;

      .col-sm-3 {
        padding: 0;
        
        img{
          width: 100%;
          height: 100%;
          box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;

          @media (max-width:575px) {
            box-shadow: none;
            
          }
      }
    }
    }

    #landing {
      background-image: url('@/assets/images/nikon.jpg');
      background-position: center;
      background-size: cover;
      background-repeat: no-repeat;
      background-attachment: fixed;
      height: 100vh;
      z-index: 100;
      overflow: hidden;


      h1 {
        position: absolute;
        font-weight: 100;
        left: .8em;
        bottom: 20%;
        z-index: 95;
        font-size: 5.5em;
        text-align: initial;
        text-transform: uppercase;

        @media (max-width: 780px) {
          font-size: 50px;
          left: 20px;
        }
      }

      button {
        position: absolute;
        left: 4.5em;
        bottom: 15%;
        text-transform: uppercase;
        font-weight: 600;
        border: none;
        padding: 10px;
        background: rgba($color: #ffffff, $alpha: .8);
        transition: .5s ease all;

        &:hover {
          color: #ffffff;
          background: rgba($color: #000000, $alpha: .8);
          transition: .8s ease all;
        }

        @media (max-width: 780px) {
          left: 20px;
        }
      }


    }
  }
</style>