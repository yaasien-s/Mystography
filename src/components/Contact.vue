<template>
    <div class="contact">
        <div class="row">
            <div class="col-sm-6 mb-4">
                <h1>Want to know more? <br> Please Drop a Message</h1>
                <br>
                <p>Get in touch and let me know how i can help. Fill out the form and i’ll be in touch as soon as
                    possible.</p>
                <br>
                <ul>
                    <i class="fa-solid fa-location-dot"></i> <label for="">Address:</label>
                    <li>Cape Town, South Africa</li>
                    <br>
                    <i class="fa-solid fa-phone"></i> <label for="">Phone:</label>
                    <li>(021) 5071 721</li>
                    <br>
                    <i class="fa-solid fa-envelope"></i> <label for="">Email:</label>
                    <li>mystography@gmail.com</li>
                </ul>
            </div>
            <div class="col-sm-6">
                <form @submit.prevent="handleSubmit" autocomplete="on" action="POST" class="text-dark">
                    <h1 class="text-initial">Contact Us</h1>
                    <label for="">Name</label>
                    <input type="name" v-model="name" required>
                    <label for="">Email</label>
                    <input type="email" v-model="email" required>
                    <label for="">Contact No.</label>
                    <input type="contact" v-model="contact" required>
                    <label for="">Message</label>
                    <textarea name="message" v-model="message" id="message" cols="20"></textarea>
                    <button type="submit" class="my-4">Send</button>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                name: "",
                email: "",
                subject: "",
                message: "",
            }
        },
        methods: {
            handleSubmit() {
                console.log(`form submitted`)
                console.log(this.name)
                console.log(this.email)
                console.log(this.message)
                fetch('https://projects-backend-yaasien.herokuapp.com/contact', {
                        method: "POST",
                        body: JSON.stringify({
                            name: this.name,
                            email: this.email,
                            message: this.message,
                        }),
                        headers: {
                            "Content-type": "application/json; charset=UTF-8"
                        },
                    })
                    .then((response) => response.json())
                    .then((json) => {
                        alert(json.msg)
                        this.name = "",
                            this.email = "",
                            this.contact = "",
                            this.message = ""
                    })
                    .catch((e) => alert(e.msg));
            },
        }
    }
</script>

<style lang="scss" scoped>
    $textcolor: white;
    $mobilecolor: black;

    .contact {
        padding-top: 125px;

        @media (max-width: 375px) {
            padding-top: 100px;
        }
    }

    .row {
        width: 95%;
        margin-inline: auto;

        ul {
            margin-left: -2em;

            li {
                list-style: none;
                margin-left: 20px;
            }
        }

        form {
            display: grid;
            width: 100%;
            margin-inline: auto;
            color: $textcolor;

            @media (max-width: 1000px) {
                width: 50%;
            }

            @media (max-width: 780px) {
                width: 50%;
                color: $mobilecolor;
            }

            @media (max-width: 375px) {
                width: 75%;
            }


            label {
                margin: 10px;
                margin-left: 0;
            }

            input {
                background: transparent;
                border: none;
                border-bottom: 2px solid #000;

                &:focus {
                    outline: none;
                }
            }

            textarea {
                background: transparent;
                border: none;
                border-bottom: 2px solid #000;
            }

            button {
                height: 50px;
                border: none;
                font-weight: 600;
                background-image: url("@/assets/images/compass.jpg");
                transition: .8s ease all;
                background-position: center;
                background-size: cover;


                &:hover {
                    background-image: url("@/assets/images/sky.jpg");
                    background-position: center;
                    background-size: cover;
                    transition: .8s ease all;
                    color: #fff;
                }
            }

        }
    }
</style>