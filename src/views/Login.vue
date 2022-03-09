<template>
    <div class="login">
        <h1 class="text-center">Login</h1>

        <form @submit.prevent="login" id="login-form">
            <label for="">Email</label>
            <input type="email" name="" id="" v-model="email" required>

            <label for="">Password</label>
            <input type="password" name="" id="" v-model="password" required>

            <button type="submit" class="my-4" @click="login">Sign in</button>

            <p style="font-weight: 600;">Not a member? <a href="#register">Create an account</a></p>
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
    .login {
        padding-top: 100px;
    }

    #login-form {
        display: grid;
        width: 40%;
        margin-inline: auto;
        background: transparent;
        padding: 50px;



        label {
            text-align: initial;
            margin: 10px;
            font-weight: 600;
            margin-left: 0;
        }

        input {
            border: none;
            border-bottom: 1px solid #000;
            background: transparent;
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


    @media (max-width: 1000px) {
        #login-form {
            width: fit-content;
        }
    }
</style>