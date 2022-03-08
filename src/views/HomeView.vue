<template>
  <carousel>
  <input type="radio" id="page1cb" checked name="pages" />
  <input type="radio" id="page2cb" name="pages" />
  <input type="radio" id="page3cb" name="pages" />
  <input type="radio" id="page4cb" name="pages" />
  <input type="radio" id="page5cb" name="pages" />
  <!-- page 1 -->
  <page id="page1">
        <img src="@/assets/mystlogo.png" alt="PUPPY">
    <label for="page2cb" title="Start"><b>Background</b></label>
  </page>
  <!-- page 2 -->
  <page id="page2">
    <div>Page Two!</div>
    <label for="page3cb" title="Next"><b>Background</b></label>
  </page>
  <!-- page 3 -->
  <page id="page3">
    <div>Page Three!</div>
    <label for="page4cb" title="Next"><b>Background</b></label>
  </page>
  <!-- page 4 -->
  <page id="page4">
    <div>Page Four!</div>
    <label for="page5cb" title="Next"><b>Background</b></label>
  </page>
  <!-- page 5 -->
  <page id="page5">
    <div>Page Five!</div>
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
    img{
      width: 100%;
      height: 100vh;
      object-fit: cover;
    }
    label {
      cursor: pointer;
      background: #d9ff4f;
      padding: 10px;
      position: absolute;
      width: fit-content;
      margin-inline: auto;
    bottom: 2em;
    left: 0;
    right: 0;
    }
  }
  @for $i from 1 through 5 {
    #page#{$i}cb:checked ~ {
      #page#{$i} {
        transform: scale(1);
      }
    }
  }
}

</style>