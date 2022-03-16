<template>
    <footer>
        <p>© 2022 MYS'TOGRAPHY ALL RIGHTS RESERVED</p>
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
        position: fixed;
        bottom: 0;
        width: 100%;
        z-index: -5;

        @media (max-width: 1000px) {
            padding-bottom: 0;
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