<template>
    <div class="register" @submit.prevent="register">

        <form action="">
            <h1 class="text-initial">Create An Account</h1>
            <label for="">Full Name <span>*</span></label>
            <input type="name" required v-model="fullname">

            <div class="row">
                <div class="col-sm-6">
                    <label for="">Email <span>*</span></label>
                    <input class="w-100" type="email" required v-model="email">
                </div>

                <div class="col-sm-6">
                    <label for="">Contact Number <span>*</span></label>
                    <input class="w-100" type="contact" required v-model="contact">
                </div>
            </div>

            <label for="">Password <span>*</span></label>
            <input type="password" required v-model="password">

            <button type="submit" class="my-4">Sign Up</button>

            <p>Already a member? <a href="#login" style="font-weight: 600;">Sign in</a></p>
        </form>

    </div>
</template>

<script>
    export default {
        data() {
            return {
                fullname: "",
                email: "",
                contact: "",
                password: "",
            };
        },
        methods: {
            register() {
                fetch("https://collab-backend-pos.herokuapp.com/users", {
                        method: "POST",
                        body: JSON.stringify({
                            fullname: this.fullname,
                            email: this.email,
                            contact: this.contact,
                            password: this.password,
                        }),
                        headers: {
                            "Content-type": "application/json; charset=UTF-8",
                        },
                    })
                    .then((response) => response.json())
                    .then((json) => {
                        this.msg = `${ this.name } registered Successfully`;
                        alert("redirecting to Explore page...");
                        localStorage.setItem("jwt", json.jwt);
                        this.$router.push({
                            name: "Explore"
                        });
                    })
                    .catch((err) => {
                        alert(err);
                    });
            },
        },
    };
</script>

<style lang="scss" scoped>
    $textcolor: white;
    $mobilecolor: black;

    * {

        // color: $textcolor;
        @media (max-width: 780px) {
            color: $mobilecolor;
        }
    }

    .register {
        padding-top: 125px;
        color: #fff;

        @media (max-width: 375px) {
            padding-top: 100px;
            padding-bottom: 80px;
        }
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