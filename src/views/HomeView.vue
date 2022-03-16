<template>
  <carousel>
    <input type="radio" id="page1cb" checked name="pages" />
    <input type="radio" id="page2cb" name="pages" />
    <input type="radio" id="page3cb" name="pages" />
    <input type="radio" id="page4cb" name="pages" />
    <input type="radio" id="page5cb" name="pages" />
    <input type="radio" id="page6cb" name="pages" />
    <input type="radio" id="page7cb" name="pages" />
    <input type="radio" id="page8cb" name="pages" />
    <input type="radio" id="page9cb" name="pages" />
    <input type="radio" id="page10cb" name="pages" />

    <!-- page 1 -->
    <page id="page1">
          <h1 class=" text-light">Welcome to MYS'Tography</h1>
      <img src="@/assets/images/lion.jpg" alt="">
      <label for="page2cb" title="Start"><b>Click Me</b> <i class="fa-solid fa-images"></i></label>
    </page>
    <!-- page 2 -->
    <page id="page2">
          <h1 class=" text-light">Welcome to MYS'Tography</h1>
      <img src="@/assets/images/camera.jpg" alt="">
      <label for="page3cb" title="Next"><b>Click Me</b> <i class="fa-solid fa-images"></i></label>
    </page>
    <!-- page 3 -->
    <page id="page3">
          <h1 class=" text-light">Welcome to MYS'Tography</h1>
      <img src="@/assets/images/book.jpg" alt="">
      <label for="page4cb" title="Next"><b>Click Me</b> <i class="fa-solid fa-images"></i></label>
    </page>
    <!-- page 4 -->
    <page id="page4">
          <h1 class=" text-light">Welcome to MYS'Tography</h1>
      <img src="@/assets/images/crystal-ball.jpg" alt="PUPPY">
      <label for="page5cb" title="Next"><b>Click Me</b> <i class="fa-solid fa-images"></i></label>
    </page>
    <!-- page 5 -->
    <page id="page5">
          <h1 class=" text-light">Welcome to MYS'Tography</h1>
      <img src="@/assets/images/blur.jpg" alt="">
      <label for="page6cb" title="Next"><b>Click Me</b> <i class="fa-solid fa-images"></i></label>
    </page>
    <!-- page 6 -->
    <page id="page6">
          <h1 class=" text-light">Welcome to MYS'Tography</h1>
      <img src="@/assets/images/nikon.jpg" alt="">
      <label for="page7cb" title="Next"><b>Click Me</b> <i class="fa-solid fa-images"></i></label>
    </page>
    <!-- Page 7 -->
    <page id="page7">
          <h1 class=" text-light">Welcome to MYS'Tography</h1>
      <img src="@/assets/images/jaguar.jpg" alt="">
      <label for="page8cb" title="Next"><b>Click Me</b> <i class="fa-solid fa-images"></i></label>
    </page>
    <!-- page 8 -->
    <page id="page8">
          <h1 class=" text-light">Welcome to MYS'Tography</h1>
      <img src="@/assets/images/ocean.jpg" alt="">
      <label for="page9cb" title="Next"><b>Click Me</b> <i class="fa-solid fa-images"></i></label>
    </page>
    <!-- page 9 -->
    <page id="page9">
          <h1 class=" text-light">Welcome to MYS'Tography</h1>
      <img src="@/assets/images/iceland.jpg" alt="">
      <label for="page10cb" title="Next"><b>Click Me</b> <i class="fa-solid fa-images"></i></label>
    </page>
    <!-- page 10 -->
    <page id="page10">
          <h1 class=" text-light">Welcome to MYS'Tography</h1>
      <img src="@/assets/images/sky.jpg" alt="">
      <label for="page1cb" title="That's all folks!"><b>Click Me</b> <i class="fa-solid fa-images"></i></label>
    </page>
  </carousel>
</template>

<script>
  // @ is an alias to /src

  export default {

  }
</script>
<style lang="scss" scoped>
$primarytext: red;
  carousel {
    width: 100%;
    text-align: center;
    display: block;
    font-size: 2rem;

    h1 {
      position: absolute;
      font-weight: 100;
      left: 30px;
      bottom: 40%;
      z-index: 95;
      font-size: 2.5em;
      
      @media (max-width: 780px) {
        font-size: 50px;
        left: 10px;
      }
    }

    input {
      display: none;
    }

    page {
      position: absolute;
      // top: 4em;
      left: 0;
      width: 100%;
      transition: transform 0.5s;
      transform: scale(0);


      img {
        width: 100%;
        height: 100vh;
        object-fit: cover;

        @media (max-width: 375px) {
          overflow: hidden;
          height: 107.8vh;
          width: 107.8vw;
        }
      }

      label {
        cursor: pointer;
        background-color: rgba(255, 255, 255, 0.5);
        color: #000;
        padding: 5px;
        position: absolute;
        width: fit-content;
        margin-inline: auto;
        bottom: 2em;
        // left: 2em;
        right: 2em;
        transition: .8s ease all;

        @media (max-width: 780px) {
          right: 1em;
          bottom: 1em;
        }

          @media (max-width: 375px) {
            right: 0;
            bottom: .7em;
          }

        &:hover {
          background-color: rgba(0, 0, 0, 0.5);
          color: #fff;
          transition: .8s ease all;
        }

        @media (max-width: 780px) {
          border-radius: 10px;
          padding: 0 5px;
        }

        i {
          // color: #000;
          display: none;

          @media (max-width: 780px) {
            display: grid;
            padding: 5px 3px;
          }

          // &:hover {
          //   color: #fff;
          // }
        }

        b {
          font-weight: 600;
            @media (max-width:780px) {
              display: none;
            }
        }
      }
    }

    @for $i from 1 through 10 {
      #page#{$i}cb:checked~ {
        #page#{$i} {
          transform: scale(1);
        }
      }
    }
  }
</style>