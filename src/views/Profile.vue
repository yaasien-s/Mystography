<template>
  <section class="Profile">
    <div class="container">
      <h2 class="testimonial text-dark pt-3">USER PROFILE</h2>
      <br><br>
        <div class="member member-box" v-if="users">
      <div class="row">
            <div class="col-sm-4">
          <i class="fa-solid fa-address-card"></i>
            </div>
          <br />
          <div class="col-sm-8">
          <h3 class=" text-dark">
            Name: {{ name }}
          </h3>
          <br />
          <h3 class="text-dark">
            Email: {{ email }}
          </h3>
          <br />
          <h3 class="text-dark">
            Contact: {{ contact }}
          </h3>
          </div>
          <br />
            <button
              type="button"
              class="button-2"
              data-bs-toggle="modal"
              data-bs-target="#exampleModal1"
            >
              Edit
            </button>
            <button class="button-1" v-on:click="deleteUser(id)">Delete</button>
        <button @click="back" id="Back">Go Back</button>
        </div>
      </div>
    </div>
  </section>

  <!-- Modal for edit  profile -->
  <div
    class="modal fade"
    id="exampleModal1"
    tabindex="-1"
    aria-labelledby="exampleModalLabel1"
    aria-hidden="true"
  >
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLabel">Edit User</h5>
          <button
            type="button"
            class="btn-close btn-danger"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
          <form @submit.prevent="updateUser">
            <div>
              NAME
              <input v-model="name" type="text" /><br />
              CONTACT
              <input v-model="contact" type="text" /><br />
              EMAIL
              <input v-model="email" type="email" /><br />
            </div>
            <div class="modal-footer">
              <button type="button" class="btn close btn-danger" data-bs-dismiss="modal">
                Close
              </button>
              <button type="submit" class="btn save btn-secondary">Save changes</button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  components: {},
  data() {
    return {
      users: null,
      name: localStorage.getItem("name"),
      contact: localStorage.getItem("contact"),
      email: localStorage.getItem("email"),
      id: localStorage.getItem("id")
    };
  },
  mounted() {
    if (!localStorage.getItem("jwt")) {
      alert("User not logged in");
      return this.$router.push({ name: "Login" });
    }
    fetch("https://collab-backend-pos.herokuapp.com/users/single-user/", {
      method: "GET",
      headers: {
        "Content-type": "application/json; charset=UTF-8",
        Authorization: `Bearer ${localStorage.getItem("jwt")}`,
      },
    })
      .then((response) => response.json())
      .then((json) => {
        console.log(json);
        this.users = json;
      })
      .catch((err) => {
        alert(err);
      });
  },
  methods: {

        back() {
    this.$router.go(-1)
        },
    updateUser() {
      if (!localStorage.getItem("jwt")) {
        alert("User not logged in");
        return this.$router.push({ name: "Login" });
      }
      fetch("https://collab-backend-pos.herokuapp.com/users/" + this.id, {
        method: "PUT",
        body: JSON.stringify({
          fullname: this.name,
          email: this.email,
          contact: this.contact,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          alert("User Updated");
          this.$router.push({ name: "Profile" });
        })
        .catch((err) => {
          alert(err);
        });
    },
    deleteUser(id) {
      if (!localStorage.getItem("jwt")) {
        alert("User not logged in");
        return this.$router.push({ name: "Login" });
      }
      fetch("https://collab-backend-pos.herokuapp.com/users/" + id, {
        method: "DELETE",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          alert("DELETED USER");
          localStorage.clear();
          this.$router.push({name:'Login'})
        })
        .catch((err) => {
          alert(err);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
.Profile {
    padding-top: 100px;

    @media (max-width:768px) {
        padding-bottom: 100px;
    }

    .row {
        border: 1px solid #000;
        border-radius: 20px;
        padding: 40px;
        width: 95%;
        margin-inline: auto;

        h3{
            @media (max-width: 768px) {
                font-size: 20px;
            }
        }

        button{
            margin: 30px auto;
            margin-bottom: 0;
            width: 15%;
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

    i{
        font-size: 8em;
        padding: 20px;
    }
}

.modal{

    form{
        font-weight: 600;
    }

    .modal-header{
        background: rgba($color: #ccc8b1, $alpha: 1.0);

    }

    .modal-body {
        background: rgba($color: #ffffff, $alpha: 1.0);

        .modal-footer{
            background: rgba($color: #ccc8b1, $alpha: 1.0);
        }
    }

    input{
        border: none;
        border-bottom: 1px solid #000;
        width: 100%;
        margin: 20px auto;
        background: transparent;

        &:focus {
            outline: none;
        }
    }
}
</style>