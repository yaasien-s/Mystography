<template>
    <div class="container">
        <h1>Explore</h1>
        <div class="row">
            <div v-for="post of posts" :key="post.id" class="card col-sm-4">
                <router-link :to="{ name: 'Post' ,params: { id: post.id } }">
                    <div class="card-body">
                        <p class="card-text">{{post.fullname}}</p>
                        <!-- <h6 style="font-weight: 600;" class="text-dark">{{post.description}}</h6> -->
                        <!-- <h5 class="card-title" style="font-weight: 600;">{{product.title}}</h5> -->
                        <!-- <p class="card-text text-dark" style="font-weight: 600;">R {{product.price}}</p> -->
                        <!-- <a href="#" class="btn" id="product-btn">Add to cart</a> -->
                    </div>
                    <img :src="post.img" class="card-img-top" alt="...">
                </router-link>
            </div>
        </div>
        <router-link :to="{name: 'CreatePost'}"><i class="far fa-plus"></i></router-link>
    </div>

</template>

<script>
    export default {
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
                                    "https://collab-backend-pos.herokuapp.com/posts" + post.id, {
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

    h1 {
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

        i {
            font-size: 4rem;
            font-weight: 600px;
            padding: 0 14px;
            position: fixed;
            right: 20px;
            bottom: 75px;
            color: #000;
            border-radius: 50%;
            background: rgba($color: #ccc8b1, $alpha: 1.0);
            transition: .8s ease all;

            &:hover {
                color: rgb(0, 0, 0);
                transition: .8s ease all;
                transform: rotate(180deg);
            }

            @media (max-width: 375px) {
                font-size: 3rem;
                padding: 0 10px;
            }
        }

    }

    .card {
        margin-inline: auto !important;
        margin-top: 125px;
        padding-bottom: 75px;
        // border-top-left-radius: 20px;
        // border-top-right-radius: 20px;
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
        background: rgba($color: #000000, $alpha: 0.8);
        text-align: initial;
        margin-left: 10px;
        border-top-left-radius: 20px;
        border-top-right-radius: 20px;



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
        border-bottom-left-radius: 20px;
        border-bottom-right-radius: 20px;
        width: 85%;
        height: 120% !important;
        object-fit: cover;
        margin-inline: auto;
        display: block;
        // width: 100%;

    }
</style>