<template>
    <div class="register" @submit.prevent="register">
        <h1 class="text-center">Create An Account</h1>

        <form action="">
            <label for="">Full Name <span>*</span></label>
            <input type="name" required v-model="fullname">

            <label for="">Email <span>*</span></label>
            <input type="email" required v-model="email">

            <label for="">Contact Number <span>*</span></label>
            <input type="contact" required v-model="contact">

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
    .register {
        padding-top: 125px;
        color: #fff;
    }

    form {
        display: grid;
        width: 35%;
        margin-inline: auto;
        background: transparent;

        @media (max-width: 1000px) {
                width: 50%;
        }

        input {
            border: none;
            border-bottom: 2px solid #000;
            background: transparent;
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