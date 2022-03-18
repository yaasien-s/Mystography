<template>
    <footer>
        <div class="row">
            <div class="col-sm-6">
          <p><router-link :to="{name: 'About'}">About Us</router-link></p>
            </div>
            <div class="col-sm-6">
        <p>© 2022 MYS'TOGRAPHY ALL RIGHTS RESERVED</p>
            </div>
        </div>
    </footer>
</template>

<script>
    export default {

    }
</script>

<style lang="scss" scoped>
    footer {
        background-color: rgba(0, 0, 0, 0.8);
        padding: 10px;
        // position: fixed;
        bottom: 0;
        width: 100%;
        // z-index: -5;

        @media (max-width: 1000px) {
            padding-bottom: 0;
        }

        .row {
            width: 100%;



            a {
                margin-inline: auto;
                text-decoration: none;
                color: #fff;
                transition: .3s ease all;

                &:hover {
                    color: #ccc8b1;
                    transition: .3s ease all;
                }
            }
        }
        // background-image: url("@/assets/images/world-map.jpg");
        // background-position: bottom;
        // background-size: cover;

        // @media (max-width: 780px) {
        //     background-image: none;
        // }

        p {
            text-align: center;
            margin-inline: auto;
            color: #fff;
        }
    }
</style>