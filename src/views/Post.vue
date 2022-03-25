<template>
        <section id="section-14" class="slide current" style="padding-top:100px">
          <div class="wrap fadeInUp" >
              
            
                            <!-- <router-link to="/editPost" class="view-btn btn border-primary" style="font-size:2rem">Edit</router-link> -->
                            <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal">
                      Edit
            </button>
            <div class="grid vertical-align" v-if="blog" style="margin-top:50px;margin-bottom:200px">
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
            <input type="text" class="form-control" id="recipient-name" v-model="body">

          </div>
          <div class="mb-3">
            <label for="message-text" class="col-form-label">Image</label>
            <input type="text" class="form-control" id="recipient-name" v-model="img">

          </div>
        </form>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary" v-on:click="editBlog(blog._id)">Edit</button>
      </div>
    </div>
  </div>
</div>
           <div class="column">
                <figure>
                  <img :src="blog.img" class="please" alt="">
                </figure>
              </div>
              <div class="column">
                <h2>
                   {{blog.title}}
                </h2>
                <p class="text-intro">{{blog.body}}</p>
                <p class="text-intro"><span><img :src="blog.avatar" alt="" class="" style="border-radius:100%;width:2%"></span> {{blog.author}}</p>
                <p class="text-intro">{{blog.date}}</p>
              </div>
              <!-- end .column-->
              <!-- end figure-->
            <router-link to="/posts" class="view-btn btn border-primary" style="font-size:2rem">Go back</router-link>
            </div>
            <!-- end .grid-->
          </div>
          <!-- end .wrap-->
      <!-- <div v-else></div> -->
        </section>
</template>

<script>
export default {
props:['id'],
data(){
  return{
    blog:null,
    search:"",
    title:"",
    body:"",
    img:""
  }
},
// mounted() {
//       fetch("http://localhost:5000/posts/", {
//         method: "GET",
//         headers: {
//           "Content-type": "application/json; charset=UTF-8",
//         },
//       })
//         .then((response) => response.json())
//         .then((json) => {
//           this.blogs = json;
//           this.blogs.forEach(async (blog) => {
//             await fetch(
//               "http://localhost:5000/users/" + blog.author,
//               {
//                 method: "GET",
//                 headers: {
//                   "Content-type": "application/json; charset=UTF-8",
//                 },
//               }
//             )
//               .then((response) => response.json())
//               .then((json) => {
//                 blog.author_name = json.name;
//               });
//           });
//         })
//         .catch((err) => {
//           res.send(err)
//         });
//   },
mounted() {
      
  fetch("https://collab-backend-pos.herokuapp.com/posts/" + this.id, {
      method: "GET",
      headers: {
        "Content-type": "application/json; charset=UTF-8",
      },
    })
      .then((response) => response.json())
      .then( (json) => {
        this.blog = json;
      });
  
  },
   methods:{
      editBlog: function(id){
      if (!localStorage.getItem("jwt")) {
        alert("User not logged in");
        return this.$router.push({ name: "Login" });
      }
      fetch("https://collab-backend-pos.herokuapp.com/posts/" + id, {
        method: "PUT",
        body: JSON.stringify({
          title: this.title,
          body: this.body,
          img:this.img
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          alert("Post Updated");
        this.$router.go()
        })
        .catch((err) => {
          alert(err);
        });
  }
}
  
}
</script>

<style scoped>
.view-btn:hover{
background-color: rgb(55, 55, 241);
color: white;
}

</style>