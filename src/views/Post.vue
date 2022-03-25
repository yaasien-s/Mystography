<template>
        <section id="section-14" class="slide current" style="padding-top:150px">
          <div class="wrap fadeInUp" >
              
            
                            <!-- <router-link to="/editPost" class="view-btn btn border-primary" style="font-size:2rem">Edit</router-link> -->
            <div class="grid vertical-align" v-if="posts">
              <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">New message</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        <form>
          <div class="mb-3">
            <label for="recipient-name" class="col-form-label">title</label>
            <input type="text" class="form-control" id="recipient-name" v-model="title">
          </div>
          <div class="mb-3">
            <label for="message-text" class="col-form-label">Description</label>
            <input type="text" class="form-control" id="recipient-name" v-model="description">

          </div>
        </form>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary" v-on:click="editPost(posts._id)">Save changes</button>
      </div>
    </div>
  </div>
</div>
<!-- end of modal -->
           <div class="container">
             <div class="row">
               <div class="col-sm-8">
                  <img :src="posts.img" class="please" alt="">
               </div>
               <div class="col-sm-4">
                 <div class="post-text">
                <p class="text-intro" id="Date">{{posts.date}}</p>
                <br>
                <h2 class="display-5">
                   {{posts.title}}
                </h2>
                <br>
                <p class="text-intro">{{posts.description}}</p>
                <br>
  <button type="button" data-bs-toggle="modal" data-bs-target="#exampleModal">
Edit
</button>
                 </div>
             <button @click="back" id="Back">Go Back</button>
               </div>
             </div>
              </div>
                <!-- <p class="text-intro"><span><img :src="blog.avatar" alt="" class="" style="border-radius:100%;width:2%"></span> {{blog.author}}</p> -->
              </div>
              <!-- end .column-->
              <!-- end figure-->
            </div>
            <!-- end .grid-->
          <!-- end .wrap-->
      <!-- <div v-else></div> -->
        </section>
</template>

<script>
export default {
props:['id'],
data(){
  return{
    posts:null,
    // search:"",
    title:"",
    description:"",
    img:"",
  }
},

mounted() {
      
  fetch("https://collab-backend-pos.herokuapp.com/posts/" + this.id, {
      method: "GET",
      headers: {
        "Content-type": "application/json; charset=UTF-8",
      },
    })
      .then((response) => response.json())
      .then( (json) => {
        this.posts = json;
      });
  
  },
   methods:{
      back() {
    this.$router.go(-1)
        },
editPost() {
      if (!localStorage.getItem("jwt")) {
        alert("User not logged in");
        return this.$router.push({ name: "Login" });
      }
      fetch("https://collab-backend-pos.herokuapp.com/posts/" + this.id, {
        method: "PUT",
        body: JSON.stringify({
          title: this.title,
          description: this.description,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          alert("Post Updated");
          this.$router.push({ name: "Explore" });
        })
        .catch((err) => {
          alert(err);
        });
    },
}
  
}
</script>

<style lang="scss" scoped>
.container {

  .col-sm-8 {
    height: 500px;

    img {
      width: 100%;
      height: 75%;
      border-top-left-radius: 20px;
      border-bottom-left-radius: 20px;
      box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
      object-fit: cover;
    }
  }
  
  .col-sm-4 {
    margin-left: -23px;
  }

  .post-text{
    height: 75%;
    padding: 30px;
    border-top-right-radius: 20px;
    border-bottom-right-radius: 20px;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;

    h2 {
      font-weight: 600;
    }

    p {
      font-size: 1.2rem;
      font-weight: 600;
    }

    button {
       margin: 30px auto;
            margin-bottom: 0;
            width: 35%;
            font-weight: 600;
            padding: 10px;
            border: none;
            background: rgba($color: #ffffff, $alpha: .8);
            color: #000000;
            transition: .5s ease all;
            border-radius: 10px;

            &:hover {
                background: rgba($color: #000000, $alpha: .8);
                transition: .5s ease all;
                color: #ffffff;
            }
    }

  }
  #Back{
    position: absolute;
    right: 50px;
           margin: 30px auto;
            margin-bottom: 0;
            width: 10%;
            font-weight: 600;
            border-radius: 10px;
            padding: 10px;
            border: none;
            background: rgba($color: #ffffff, $alpha: .8);
            color: #000000;
            transition: .5s ease all;

            &:hover {
                background: rgba($color: #000000, $alpha: .8);
                transition: .5s ease all;
                color: #ffffff;
            }
  }
}

</style>