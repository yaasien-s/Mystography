<template>
    <div class="container">
        <h1>Explore</h1>
        <div class="row">
            <div v-for="post of posts" :key="post.title" class="card col-sm-4">
                    <img :src="post.img" class="card-img-top" alt="...">
                        <router-link :to="{name: 'Post', params: { id: post._id }}">
                            <i class="fa-solid fa-circle-info"></i>
                        </router-link>
                    <div class="card-body">
                        <p class="card-text">{{post.created_by}}</p>
                    </div>
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
                fetch("https://collab-backend-pos.herokuapp.com/posts", {
                        method: "GET",
                        headers: {
                            "Content-type": "application/json; charset=UTF-8",
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
            }

    };
</script>

<style lang="scss" scoped>
    $textcolor: white;
    $mobilecolor: black;

    h1 {
        color: $mobilecolor;
        margin-bottom: -100px;
    }

    .container {
        padding-top: 125px;
        padding-bottom: 125px;
        // column-count: 3;
        // column-gap: 20px;

        .fa-plus {
            font-size: 4rem;
            font-weight: 600px;
            padding: 0 14px;
            position: fixed;
            right: 20px;
            bottom: 100px;
            color: #000;
            border: 1px solid #000;
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
        // padding-bottom: 35px;
        // border-top-left-radius: 20px;
        // border-top-right-radius: 20px;
        background: transparent;
        border: none;
        // z-index: -10;
        display: inline-block;
        // width: 100%;

        h6 {
            position: absolute;
            right: 40px;
            bottom: 0;
        }
        .fa-circle-info{
            position: absolute;
            font-size: 2em;
            left: 60px;
            top: 20px;
            border: none;
            background: none;
            color: #ccc8b1;
            transition: .5s ease all;

            &:hover {
                color: #fff;
                transition: .5s ease all;
                transform: scale(1.1) translateY(-5px);
            }

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
        border-bottom-left-radius: 20px;
        border-bottom-right-radius: 20px;



        .text-secondary {
            // color: #9A6D38 !important;
            font-weight: 600;
        }

        p {
            color: $textcolor;

        }

    }


    .card-img-top {
        border-top-left-radius: 20px;
        border-top-right-radius: 20px;
        width: 85%;
        height: 400px !important;
        object-fit: cover;
        margin-inline: auto;
        display: block;
        // width: 100%;

    }
</style>