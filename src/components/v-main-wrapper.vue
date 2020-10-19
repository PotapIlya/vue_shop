<template>
    <div class="v-main-wrapper">
        <h1>Main</h1>
        <keep-alive>
            <router-view></router-view>
        </keep-alive>
    </div>
</template>

<script>
    export default {
        name: "v-main-wrapper",

        props: {
            cart_data: {
                type: Array,
                default() {
                    return [];
                }
            }
        }
    }
</script>

<style lang="scss">

    .v-main-wrapper{
        width: 1000px;
        margin: 0 auto;
    }

</style>