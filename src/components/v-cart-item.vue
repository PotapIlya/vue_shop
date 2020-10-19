<template>
    <div class="v-cart-item">
        <img class="v-cart-item__img" :src="require(`../assets/images/${cart_item_data.image}`)" alt="">
        <p>{{ cart_item_data.name }}</p>
        <p>{{ cart_item_data.price }}</p>
        <p>{{ cart_item_data.article }}</p>
        <div class="v-cart-item__quantity">
            <p>Кол-во</p>
            {{ cart_item_data.quantity }}
        </div>
        <button @click="deleteFromCart">Удалить</button>
    </div>
</template>

<script>
    export default {
        name: "v-cart-item",
        props: {
            cart_item_data: {
                type: Array,
                default(){
                    return{}
                }
            }
        },
        mounted(){
            this.$set(this.cart_item_data, 'quantity', 1)
        },
        methods: {
            deleteFromCart(){
                this.$emit('deleteFromCart')
            },
        }
    }
</script>

<style lang="scss">
    .v-cart-item{
        display: flex;
        justify-content: space-around;
        align-items: center;
        flex-wrap: nowrap;
        box-shadow: 0 0 8px #000;
        padding: $padding*2;
        margin: $margin*2;

        &__img{
            max-width: 50px;
        }
        button{
            padding: 10px 20px;
            border: 1px solid #999;
            background: transparent;
            border-radius: 10px;
        }
    }
</style>