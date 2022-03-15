<template>
    <div class="container">
        <h1>Explore</h1>
        <div class="row">
            <div v-for="post of posts" :key="post.name" class="card col-sm-3">
                <img :src="post.img" class="card-img-top" alt="...">
                <div class="card-body">
                    <p class="card-text">{{post.fullname}}</p>
                    <!-- <h6 style="font-weight: 600;" class="text-dark">{{post.description}}</h6> -->
                    <!-- <h5 class="card-title" style="font-weight: 600;">{{product.title}}</h5> -->
                    <!-- <p class="card-text text-dark" style="font-weight: 600;">R {{product.price}}</p> -->
                    <!-- <a href="#" class="btn" id="product-btn">Add to cart</a> -->
                </div>
            </div>
        </div>
        <Modal :modalActive="modalActive">
            <div class="modal-content">
                <h1>Header</h1>
                <p>Message</p>
            </div>
</Modal>
    </div>

</template>

<script>
import Modal from '@/components/Modal.vue'
import { ref } from 'vue';
    export default {
        components: {
            Modal,
        },
        setup() {
            const modalActive = ref(true)

            return { modalActive };
        },
        data() {
            return {
                posts: null,
            };
        },
        // fetching post
        created() {
            if (localStorage.getItem("jwt")) {
                fetch("https://collab-backend-pos.herokuapp.com/posts", {
                        method: "GET",
                        headers: {
                            "Content-type": "application/json; charset=UTF-8",
                            Authorization: `Bearer ${localStorage.getItem("jwt")}`,
                        },
                    })
                    .then((response) => response.json())
                    .then((json) => {
                        this.posts = json;
                        this.posts.forEach(async (post) => {
                            await fetch(
                                    "https://collab-backend-pos.herokuapp.com/posts" + post.fullname, {
                                        method: "GET",
                                        headers: {
                                            "Content-type": "application/json; charset=UTF-8",
                                            Authorization: `Bearer ${localStorage.getItem("jwt")}`,
                                        },
                                    }
                                )
                                .then((response) => response.json())
                                .then((json) => {
                                    post.author = json.name;
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
    margin-bottom: -100px;

    @media (max-width:780px) {
        color: $mobilecolor;
    }
}
    .container {
        padding-top: 125px;
        padding-bottom: 125px;
        // column-count: 3;
        // column-gap: 20px;

    }

    .card {
        margin-inline: auto !important;
        margin-top: 125px;
        padding-bottom: 75px;
        border-bottom-left-radius: 20px;
        border-bottom-right-radius: 20px;
        background: transparent;
        border: none;
        z-index: -10;
        display: inline-block;
        // width: 100%;

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
        background: rgba($color: #000000, $alpha: 0.5);
        text-align: initial;
        margin-left: 10px;
        border-bottom-left-radius: 20px;
        border-bottom-right-radius: 20px;



        .text-secondary {
            // color: #9A6D38 !important;
            font-weight: 600;
        }

        p {
            color: $textcolor;

            @media (max-width: 780px) {
                color: $mobilecolor;
                font-weight: 600;
            }
        }
    }


    .card-img-top {
        border-top-left-radius: 20px;
        border-top-right-radius: 20px;
        width: 85%;
        height: 120%;
        object-fit: cover;
        margin-inline: auto;
        display: block;
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