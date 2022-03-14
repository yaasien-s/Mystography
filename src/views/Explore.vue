<template>
    <div class="container">
        <h1>Explore</h1>
        <div class="row">


            <div v-for="product of products" :key="product.name" class="card mx-5 my-5 col-sm-3 p-0">
                <img :src="product.img" class="card-img-top" alt="...">
                    <h6 style="font-weight: 600;" class="text-dark">{{product.description}}</h6>
                <div class="card-body">
                    <!-- <h5 class="card-title" style="font-weight: 600;">{{product.title}}</h5> -->
                    <!-- <p class="card-text text-secondary">{{product.category}}</p> -->
                    <!-- <p class="card-text text-dark" style="font-weight: 600;">R {{product.price}}</p> -->
                    <!-- <a href="#" class="btn" id="product-btn">Add to cart</a> -->
                </div>
            </div>

        </div>
    </div>
<Modal/>

</template>

<script>
import Modal from '@/components/Modal.vue'
    export default {
        components: {
            Modal,
        },
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
                                    "https://collab-backend-pos.herokuapp.com/products" + product
                                    .name, {
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
$textcolor: white;
$mobilecolor: black;

h1{
    color: $textcolor;

    @media (max-width:780px) {
        color: $mobilecolor;
    }
}
    .container {
        padding-top: 125px;
        column-count: 3;
        column-gap: 20px;

    }

    .card {
        margin-inline: auto;
        border-bottom-left-radius: 20px;
        border-bottom-right-radius: 20px;
        background: transparent;
        border: none;
        z-index: -10;
        // display: inline-block;
        width: 100%;

        h6 {
            position: absolute;
            right: 40px;
            bottom: 0;
        }

    }

    .card-body {
        /* border-top: 2px solid black; */
        // margin-top: 5px;
        width: 85%;
        margin-inline: auto !important;
        background: #fff;
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
        // display: block;
        // width: 100%;

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