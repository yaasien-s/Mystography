<template>
 <div class="container">
<h1>Explore</h1>
      <div class="row">


        <div v-for="product of products" :key="product.name" class="card mx-5 my-5 col-sm-3 p-0">
          <img :src="product.img" class="card-img-top" alt="...">
          <div class="card-body">
            <!-- <h5 class="card-title" style="font-weight: 600;">{{product.title}}</h5> -->
            <h6 style="font-weight: 600;">{{product.description}}</h6>
            <p class="card-text text-secondary">{{product.category}}</p>
            <p class="card-text text-dark" style="font-weight: 600;">R {{product.price}}</p>
            <a href="#" class="btn" id="product-btn">Add to cart</a>
          </div>
        </div>

      </div>
    </div>


</template>

<script>
  export default {
    data() {
      return {
        products: null,
      };
    },
    // fetching product
    created() {
      if (localStorage.getItem("jwt")) {
        fetch("https://collab-backend-pos.herokuapp.com/products", {
            method: "GET",
            headers: {
              "Content-type": "application/json; charset=UTF-8",
              Authorization: `Bearer ${localStorage.getItem("jwt")}`,
            },
          })
          .then((response) => response.json())
          .then((json) => {
            this.products = json;
            this.products.forEach(async (product) => {
              await fetch(
                  "https://collab-backend-pos.herokuapp.com/products" + product.name, {
                    method: "GET",
                    headers: {
                      "Content-type": "application/json; charset=UTF-8",
                      Authorization: `Bearer ${localStorage.getItem("jwt")}`,
                    },
                  }
                )
                .then((response) => response.json())
                .then((json) => {
                  product.author = json.name;
                });
            });
          })
          .catch((err) => {
            alert("Log in failed");
          });
      } else {
        alert("Not logged in");
        this.$router.push({
          name: "Login"
        });
      }

    },
  };
</script>

<style lang="scss" scoped>
.container {
    padding-top: 125px;
}
.card {
    margin-right: auto !important;
    margin-left: auto !important;
    border-bottom-left-radius: 20px;
    border-bottom-right-radius: 20px;
    background: transparent;
    border: none;
    z-index: -10;
  }

  .card-body {
    /* border-top: 2px solid black; */
    margin-top: 5px;
    background: transparent;
    text-align: initial;
    margin-left: 10px;


.text-secondary {
    color: #9A6D38 !important;
    font-weight: 600;
  }
  }


  .card-img-top {
    width: 85%;
    height: 85%;
    object-fit: cover;
    margin-inline: auto;

  }

  #product-btn {
    background-color: #9A6D38;
    font-weight: 600;

    
  &:hover {
    background-color: #000;
    color: #9A6D38;
    font-weight: 600;
  }
  }

</style>