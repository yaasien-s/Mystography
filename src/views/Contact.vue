<template>
<div class="contact">
  <form  @submit.prevent="handleSubmit" autocomplete="on" action="POST">
<h1 class="text-initial">Contact</h1>
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
                .then((json) => {alert(json.msg)
                this.name ="",
                this.email ="",
                this.contact="",
                this.message =""
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
}
form {
    display: grid;
    width: 35%;
    margin-inline: auto;
     color: $textcolor;

    @media (max-width: 780px) {
        width: 50%;
        color: $mobilecolor;
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
        height: 40px;
        border: none;
        font-weight: 600;
        transition: 1s ease all;
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

}
</style>