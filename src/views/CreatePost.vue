<template>
<div id="Create">
          <div id="form">
            <form @submit.prevent="addPost">
                <legend>Add Post</legend>
                <label>Title</label>
                  <input type="text" tabindex="1" name="title" required="" v-model="title">
                <label>Image URL</label>
                  <input type="text" tabindex="1" name="Image" required="" v-model="img">
                <label>Caption</label>
                  <input type="text" tabindex="1" name="caption" required="" v-model="description">
                  <button class="mt-4" type="submit" tabindex="3">Add post ›</button>
                  <br>
                  <button @click="back" id="Back" class="my-0">Go Back</button>
            </form>
          </div>
        </div>
</template>
<script>
export default {
  data() {
    return {
      title: "",
      body: "",
      img: "",
    };
  },
  methods: {

    back() {
    this.$router.go(-1)
},
    addPost() {
      if (!localStorage.getItem("jwt")) {
        alert("User not logged in");
        this.$router.push({ name: "Login" });
      }
      fetch("https://collab-backend-pos.herokuapp.com/posts", {
        method: "POST",
        body: JSON.stringify({
          title: this.title,
          description: this.description,
          img: this.img,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          alert("Post Created");
          this.$router.push({ name: "Explore" });
        })
        .catch((err) => {
          alert(err);
          this.$router.push({ name: "Login" });
        });
    },
  },
};
</script>
<style lang="scss" scoped>
#Create{
  padding-top:150px;
}

 form {
        display: grid;
        width: 35%;
        margin-inline: auto;
        background: transparent;

        @media (max-width: 1000px) {
            width: 50%;
        }

        @media (max-width: 375px) {
            width: 75%;
        }

        #Back{
          background: #505050;
          width: 25%;
          transition: .5s ease all;

          &:hover {
            background: #000;
            transition: .5s ease all;
          }
        }

        input {
            border: none;
            border-bottom: 2px solid #000;
            background: transparent;

            &:focus {
                outline: none;
            }
        }


        label {
            text-align: initial;
            margin: 10px;
            margin-left: 0;

            span {
                color: red;
            }
        }

    }

    button {
        color: #fff;
        border: none;
        height: 40px;
        transition: .8s ease all;
        font-weight: 600;
        background-image: url("@/assets/images/compass.jpg");
        background-position: center;
        background-size: cover;



        &:hover {
            background-image: url("@/assets/images/sky.jpg");
            background-position: center;
            background-size: cover;
            transition: .8s ease all;
        }
        
    }

</style>