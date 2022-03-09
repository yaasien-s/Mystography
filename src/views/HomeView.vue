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
      <img src="@/assets/images/lion.jpg" alt="">
      <label for="page2cb" title="Start"><b>Background</b></label>
    </page>
    <!-- page 2 -->
    <page id="page2">
      <img src="@/assets/images/camera.jpg" alt="">
      <label for="page3cb" title="Next"><b>Background</b></label>
    </page>
    <!-- page 3 -->
    <page id="page3">
      <img src="@/assets/images/book.jpg" alt="">
      <label for="page4cb" title="Next"><b>Background</b></label>
    </page>
    <!-- page 4 -->
    <page id="page4">
      <img src="@/assets/images/crystal-ball.jpg" alt="PUPPY">
      <label for="page5cb" title="Next"><b>Background</b></label>
    </page>
    <!-- page 5 -->
    <page id="page5">
      <img src="@/assets/images/blur.jpg" alt="">
      <label for="page6cb" title="Next"><b>Background</b></label>
    </page>
    <!-- page 6 -->
    <page id="page6">
      <img src="@/assets/images/nikon.jpg" alt="">
      <label for="page7cb" title="Next"><b>Background</b></label>
    </page>
    <!-- Page 7 -->
    <page id="page7">
      <img src="@/assets/images/studio.jpg" alt="">
      <label for="page8cb" title="Next"><b>Background</b></label>
    </page>
    <!-- page 8 -->
    <page id="page8">
      <img src="@/assets/images/ocean.jpg" alt="">
      <label for="page9cb" title="Next"><b>Background</b></label>
    </page>
    <!-- page 9 -->
    <page id="page9">
      <img src="@/assets/images/iceland.jpg" alt="">
      <label for="page10cb" title="Next"><b>Background</b></label>
    </page>
    <!-- page 10 -->
    <page id="page10">
      <img src="@/assets/images/sky.jpg" alt="">
      <label for="page1cb" title="That's all folks!"><b>Background</b></label>
    </page>
  </carousel>
</template>

<script>
  // @ is an alias to /src

  export default {

  }
</script>
<style lang="scss" scoped>
body {
  background-image: none;
}
  carousel {
    width: 100%;
    text-align: center;
    font-family: Trebuchet MS;
    display: block;
    font-size: 2rem;

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

      div {
        padding: 3em;
      }

      img {
        width: 100%;
        height: 100vh;
        object-fit: cover;
      }

      label {
        cursor: pointer;
        background-color: rgba(0, 0, 0, 0.8);
        color: #fff;
        padding: 10px;
        position: absolute;
        width: fit-content;
        margin-inline: auto;
        bottom: 2em;
        left: 0;
        right: 0;
        transition: .8s ease all;

        &:hover {
          background-color: rgba(255, 255, 255, 0.8);
          color: #000;
          transition: .8s ease all;
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