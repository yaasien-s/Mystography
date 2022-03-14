<template>
    <div class="login">

        <form @submit.prevent="login" id="login-form">
        <h1 class="text-initial">Login</h1>
            <label for="">Email</label>
            <input type="email" name="" id="" v-model="email" autocomplete="email" required>

            <label for="">Password</label>
            <input type="password" name="" id="" v-model="password" autocomplete="password" required>

            <button type="submit" class="my-4" @click="login">Sign in</button>

            <p>Not a member? <a href="#register" style="font-weight: 600;">Create an account</a></p>
        </form>

    </div>
</template>

<script>
    export default {
        data() {
            return {
                email: "",
                password: "",
            };
        },
        methods: {
            login() {
                fetch('https://collab-backend-pos.herokuapp.com/users', {
                        method: 'PATCH',
                        body: JSON.stringify({
                            email: this.email,
                            password: this.password,
                        }),
                        headers: {
                            'Content-type': 'application/json; charset=UTF-8',
                        },
                    })
                    .then((response) => response.json())
                    .then((json) => {
                        localStorage.setItem("jwt", json.jwt);
                        alert("User logged in");
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

    .login {
        padding-top: 125px;
    }

    #login-form {
        display: grid;
        width: 40%;
        margin-inline: auto;
        background: transparent;
        padding: 50px;
        color: $textcolor;

        @media (max-width: 780px) {
            color: $mobilecolor;
        }


        @media (max-width: 1000px) {
                width: 60%;
        }

        label {
            text-align: initial;
            margin: 10px;
            margin-left: 0;
        }

        input {
            border: none;
            border-bottom: 2px solid #000;
            background: transparent;

            &:focus {
                outline: none;
            }
        }
    }


    button {
        border: none;
        height: 40px;
        transition: 1s ease all;
        font-weight: 600;
        background-image: url("@/assets/images/world-map.jpg");
        background-position: bottom;
        background-size: cover;



        &:hover {
            background-image: url("@/assets/images/world-map.jpg");
            background-position: top;
            background-size: cover;
            transition: 1s ease all;
        }
    }


</style>