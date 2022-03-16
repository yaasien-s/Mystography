<template>
  <div id="Create">
    <form action="">
    <h1 class="text-initial">Create Post</h1>
    <br>
      <label for="myfile">Image</label>
      <input type="file" id="myfile" name="myfile" required />
      <br>
      <label for="">Caption</label>
      <textarea name="caption" id="caption" cols="30" rows="3"></textarea>
      <button v-on:click="submit()" class="my-3 h-75">Post</button>
    </form>
  </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
$textcolor: white;
$mobilecolor: black;
#Create{
  padding-top: 125px;
  color: $textcolor;

@media (max-width: 780px) {
  color: $mobilecolor;
}

$textcolor: white;
$mobilecolor: black;


  form {
    width: 45%;
    display: grid;
    margin-inline: auto !important;

    @media (max-width: 375px) {
      width: 75%;
    }

    input{
      background: none;
       border: none;
      border-bottom: 2px solid #000;

      &:focus {
        outline: none;
      }
    }

    textarea{
      background: none;
      border: none;
      border-bottom: 2px solid #000;

      &::placeholder {
        color: #000;
        font-weight: 600;
      }

      &:focus {
        outline: none;
      }
    }
  }

   button {
        border: none;
        font-weight: 600;
        transition: 1s ease all;
        background-image: url("@/assets/images/world-map.jpg");
        background-position: bottom;
        background-size: cover;

        
        &:hover {
            background-image: url("@/assets/images/world-map.jpg");
            background-position: top;
            background-size: cover;
            transition: 1s ease all;
        }
    }

}

</style>