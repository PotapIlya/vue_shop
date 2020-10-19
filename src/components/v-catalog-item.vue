<template>
    <div class="v-catalog-item">
        <img class="v-catalog-item__img" :src="require(`../assets/images/${product_data.image}`)" alt="">
        <p class="v-catalog-item__name">{{ product_data.name }}</p>
        <p class="v-catalog-item__price">Цена: <b>{{ product_data.price }} P</b></p>
        <button
                @click="addToCart"
                class="v-catalog-item__add_to_cart_btn btn"
        >Добавить в корзину</button>
    </div>
</template>

<script>
    export default {
        name: "v-catalog-item",
        props: {
            product_data:{
                type: Object,
                default(){
                    return{}
                }
            }
        },
        methods:{
            addToCart() {
                this.$emit('addToCart', this.product_data)
            },
        }
    }
</script>

<style lang="scss">
    .v-catalog-item{
        flex-basis: 25%;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        box-shadow: 0 0 8px #000;
        padding: $padding*2;
        margin: $margin*2;

        &__img{
            width: 100px;
        }
    }
</style>